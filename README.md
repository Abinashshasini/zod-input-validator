# 🛠️ Input Validator

A **flexible** and **powerful** input validation library designed to simplify validation for forms and APIs.  
With support for **chainable validation rules** and **schema-based object validation**, this library is a must-have for clean and efficient input handling.

---

## ✨ Features

- 🚀 **Chainable Validation Rules**: Easily validate fields with modular and readable methods.
- 📋 **Schema-Based Validation**: Validate complex objects with predefined schemas.
- ✅ **Built-in Rules**: Common validations like strings, min/max length, regex, and email included out of the box.
- 🔧 **Extensible**: Add custom rules tailored to your needs.
- ⚡ **Lightweight and Fast**: Minimal dependencies, easy integration, and excellent performance.

---

## 📦 Installation

Getting started is quick and simple! Clone the repository to include it in your project:

### Clone Repository

```bash
git clone https://github.com/Abinashshasini/input-validator.git
```

### npm install

```bash
npm i npm i zod-input-validator
```

### Yarn add

```bash
yarn add zod-input-validator
```

### Validating a Single Field

Use the `Validator` class to validate individual fields with chainable rules.

```javascript
import { Validator } from 'zod-input-validator';

const validator = new Validator('username')
  .string()
  .min(3, 'Username must be at least 3 characters long.')
  .max(20, 'Username cannot exceed 20 characters.');

const result = validator.validate('ab');
console.log(result);
// Output:
// {
//   isValid: false,
//   errors: 'Username must be at least 3 characters long.'
// }
```

#### Object Validation Example

Define a schema with validation rules for each field and validate an object against it.

```javascript
import { Validator } from 'zod-input-validator';

const schema = Validator.object({
  username: new Validator()
    .string()
    .min(3, 'Username must be at least 3 characters long.')
    .max(20, 'Username cannot exceed 20 characters.'),
  emaiil: new Validator().isEmail('Please provide a valid email address.'),
});

const result = schema.parse({
  username: 'te',
  emaiil: 'test.com',
});
const result = validator.parse(data);
console.log(result);
// Output:
// {
//   isValid: false,
//   errors: {
//     username: 'Username must be at least 3 characters long.',
//     email: 'Please provide a valid email address.'
//   }
// }
```
