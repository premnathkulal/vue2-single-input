# Vue Single input

Vue single input takes only one input in a box used for taking OTP, MPIN inputs.

## Installing

Using npm:

```bash
$ npm install vue-single-input
```

Using yarn:

```bash
$ yarn add vue-single-input
```

## Usage

import in index.ts / index.js

```js
import SingleInput from "vue-single-input";
```

add to Vue

```js
Vue.use(SingleInput);
```

Than use anywhere in template

```html
<SingleInput formId="your-form-id" />
```

> **NOTE:** **formId** is required

## Example

```html
<SingleInput
  v-model="myMpin"
  formId="id"
  :boxCount="4"
  textColor="green"
  borderColor="red"
  textSize="2em"
  :withBorder="false"
  borderRadius="0%"
  backgroundColor="none"
  type="text"
/>
```

### output

## Options

- **v-model** : Takes Variable name given by developer

- **formId** : **Required** form Id given by developer

- **boxCount** : Type is number

- **textColor** : Takes any valid color given by developer.
  Ex: red, green, '#ff00ff', 'rgba(1, 1, 0, 0.5)'

- **borderColor** : Takes any valid color given by developer.
  Ex: red, green, '#ff00ff', 'rgba(1, 1, 0, 0.5)'

- **textSize** : Ex: 2rem, 3em, 1px, 4px

- **withBorder** : Takes boolen values **true** or **false**

- **borderRadius** : Ex: 10%, 50%, 2rem, 3em, 1px, 4px

- **backgroundColor** : Takes any valid color given by developer.
  Ex: red, green, '#ff00ff', 'rgba(1, 1, 0, 0.5)'

- **type** : Ex: number, password, text

## License

![alt text](https://drive.google.com/file/d/1OT87T1rrOUrlcwEI_wonoexQG-wYYL4C/view?usp=sharing)
