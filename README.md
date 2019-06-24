# Faker Factory

A small utility for creating fake models using a factory function. This factory is inspired by Laravel's factory function that will work with Mongoose models.

### Example Registration

Register a factory by providing `label`, `class` and `callback` arguments. The callback function provides an instance of
[Faker.js](https://github.com/marak/Faker.js/) and should return an object of attributes for your model.

```js
const factory = require("faker-factory");

// Your mongoose User model
const User = require("./models/user");

factory.register("user", User, faker => {
  return {
    firstName: faker.name.firstName(),
    lastName: faker.name.lastName(),
    email: faker.internet.email()
  };
});
```

### Example Factory Instance

Once you've registered your factory bindings, you can make as many models as you like, each with unique data. You can
also replace the default attributes with your own.

```js
const factory = require("faker-factory");

let users = factory("user", 10).make(); // array of fake users
let adminUsers = factory("user", 10).make({ isAdmin: true }); // array of fake admin users
```

### Instructions For Using Faker Factory

The factory assumes that you are using Mongoose ODM.
