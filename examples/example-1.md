# Example 1

Suppose we have an object Car, with the following structure:

```
class Car {
    var color
    var width
    var user
    
    void buy()
    void sell()
    void startEngine()
}
```

## Negative Example

Here is an example of a documentation containing this smell:

> #### Car Class Documentation
>
> The `Car` class represents a car with various attributes and actions that can be performed on it.
>
> **Attributes**
>
> * **color**: The color of the car. This is a string that can represent any valid color.
> * **width**: The width of the car in centimeters. This is a number that should be between 100 and 300 cm.
> * **user**: The current user of the car. This is an object representing the user.
>
> **Methods**
>
> * **buy()**: This method allows a user to buy the car. When the car is bought, the `user` attribute is set to the new owner.
> * **sell()**: This method allows the current owner to sell the car. When the car is sold, the `user` attribute is set to `null`.
> * **startEngine()**: This method starts the engine of the car. Internally, it checks if the `user` is set and if the `color` is a valid color before starting.
>
> **Internal Structure (Excess Information)**
>
> * The `color` attribute is stored as a private variable within the class and is manipulated via getter and setter methods internally.
> * The `width` attribute is validated to ensure it is within a realistic range (100 to 300 cm) whenever it is set.
> * The `user` attribute is an instance of a `User` class, which has its own set of attributes like `name`, `age`, and `licenseNumber`.
> * The `buy()` method involves complex logic to check the availability of the car in the inventory before setting the `user`.
> * The `sell()` method also handles the process of checking if the car is listed on any third-party sales platform and removes it if it is.
> * The `startEngine()` method interacts with a simulated engine object that ensures all conditions are met for starting the engine.

In the first too sections, the attributes and methods get a context description of what they are, as they should. However, the descriptions also contain the type of value or how the function operate, which may already be a bit too much internal detail.&#x20;

Meanwhile, the main problem is clearly the last section, which gives too much detail on how the variables and methods work internally (e.g., "is stored as a private variable", "also handles the process of...").

## Positive Example

In this case, the simple way to avoid this smell, is just to remove the last section. The first too are already enough detail for any developer that may need to use our API, and depending on how strict the definition of the smell you are going for, they can also be simplified.

>
>
> #### Car Class Documentation
>
> The `Car` class allows you to manage and interact with a car, including buying, selling, and starting the engine.
>
> **Attributes**
>
> * **color**: The color of the car.
> * **width**: The width of the car.
> * **user**: The current user of the car.
>
> **Methods**
>
> * **buy()**: Buys the car, setting the current user as the owner.
> * **sell()**: Sells the car, removing the current owner.
> * **startEngine()**: Starts the engine of the car.

