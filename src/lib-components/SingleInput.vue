<template>
  <div class="mpin-container">
    <template v-for="item in boxCount" class="">
      <input
        :id="formId + item"
        :key="item"
        :type="type"
        :readonly="item === 1 ? false : true"
        :autofocus="item === 1 ? true : false"
        :style="{
          textShadow: textShadow,
          border: border,
          borderBottom: borderBottom,
          fontSize: textSize,
          borderRadius: borderRadius,
          background: backgroundColor,
        }"
        inputmode="numeric"
        @input="manageMpinInput"
        @keyup.backspace="backspaceEvent"
        @keypress="isNumber($event)"
      />
    </template>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator";

@Component
export default class SingleInput extends Vue {
  fullMpin: string[] = [];
  textShadow = "0 0 0 blue";
  borderBottom = "2px solid blue";
  border = "none";
  background = "none";

  @Prop({ default: "id", required: true }) formId: string = "";
  @Prop({ default: 1 }) boxCount: number = 0;
  @Prop({ default: "blue" }) textColor: number = 0;
  @Prop({ default: "blue" }) borderColor: number = 0;
  @Prop({ default: "2em" }) textSize: string = "";
  @Prop({ default: false }) withBorder: boolean = false;
  @Prop({ default: "0%" }) borderRadius: string = "";
  @Prop({ default: "0%" }) backgroundColor: string = "";
  @Prop({ default: "text" }) type: string = "";

  // @Prop({ default: "id", required: true }) formId!: string;
  // @Prop({ default: 1 }) boxCount!: number;
  // @Prop({ default: "blue" }) textColor!: number;
  // @Prop({ default: "blue" }) borderColor!: number;
  // @Prop({ default: "2em" }) textSize!: string;
  // @Prop({ default: false }) withBorder!: boolean;
  // @Prop({ default: "0%" }) borderRadius!: string;
  // @Prop({ default: "0%" }) backgroundColor!: string;
  // @Prop({ default: "text" }) type!: string;

  manageMpinInput(event: KeyboardEvent): void {
    const target = event.target as HTMLInputElement;
    if (target.value == null || target.value == "") {
      this.fullMpin.pop();
      if (this.fullMpin.length) {
        target.readOnly = true;
        this.foucusOnSiblingInput(target.previousSibling as HTMLInputElement);
      }
    } else {
      const digit = target.value[target.value.length - 1];
      target.value = digit;
      this.fullMpin[+target.id.slice(-1) - 1] = target.value;
      if (this.fullMpin.length < this.boxCount) {
        target.readOnly = true;
        this.foucusOnSiblingInput(target.nextSibling as HTMLInputElement);
      }
    }
    this.$emit("input", this.fullMpin.join(""));
  }

  foucusOnSiblingInput(element: HTMLInputElement | null): void {
    if (element) {
      element.readOnly = false;
      element.focus();
    }
  }

  backspaceEvent(event: KeyboardEvent): void {
    event = (event ? event : window.event) as KeyboardEvent;
    const target = event.target as HTMLInputElement;
    if (target.value === "" || target.value === null) {
      if (this.fullMpin.length > 0) {
        const previousSibling = target.previousSibling as HTMLInputElement;
        this.foucusOnSiblingInput(previousSibling);
        target.readOnly = true;
      }
    }
  }

  isNumber(evt: KeyboardEvent) {
    if (this.type === "number") {
      evt = (evt ? evt : window.event) as KeyboardEvent;
      const charCode = evt.keyCode;
      if (
        charCode > 31 &&
        (charCode < 48 || charCode > 57) &&
        charCode !== 46
      ) {
        evt.preventDefault();
      } else {
        return true;
      }
    }
    return true;
  }

  created() {
    this.textShadow = `0 0 0 ${this.textColor}`;
    this.borderBottom = `${2}px solid ${this.borderColor}`;
    this.border = this.withBorder ? `${2}px solid ${this.borderColor}` : "none";
  }
}
</script>

<style lang="scss" scoped>
.mpin-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 5rem;
  input {
    color: transparent;
    text-align: center;
    box-shadow: none;
    height: 1em;
    outline: none;
    width: 2.5rem;
    margin-right: 1rem;
    &:last-child {
      margin-right: 0px;
    }
    &:focus {
      border-width: 4px !important;
    }
  }
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
input[type="number"] {
  -moz-appearance: textfield;
}
</style>
