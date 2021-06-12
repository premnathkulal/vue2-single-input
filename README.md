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

### Output

![alt text](https://drive.google.com/uc?id=1AXP4kL1DBL7kjDsv0RtYyDQ43K9-ILnc)  
![alt text](https://drive.google.com/uc?id=19lnrdc30raVbTpZh8y2nH7nkMkTLb3VJ)  
![alt text](https://drive.google.com/uc?id=11ndSN0w6T_0dTSBaFOBJDcpXWKTUvYo-)  
![alt text](https://drive.google.com/uc?id=1KJgM26YMTN36EU2w-MkPcKw2kMqvNYmK)  
![alt text](https://drive.google.com/uc?id=1OT87T1rrOUrlcwEI_wonoexQG-wYYL4C)

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
