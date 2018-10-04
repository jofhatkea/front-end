# JavaScript Classes

This is intended as a short introduction, it'll just cover what we need to get started with React. For a thorough explanation, see https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes

## General Concept

A class is a description of something. Think of it as a code-template or blueprint of a thing. When we use classes, we get what's called an object.

Classes model something, and we try to build our classes so they can model every instance of that thing.

The classic examples are cars and animals. For cars we can derive some common properties that is true for all cars, like

1. Make
2. Model
3. Color
4. Fuel Type

No matter which car we're talking about, it will have all of the above. Code wise, it looks like this

```js
class Car {
    constructor(){
        this.make = "Citroen";
        this.model = "Berlingo";
        this.color: "Blue";
        this.fuelType = "Diesel";
    }
}
```

Just like regular objects (object literals) we can access the properties using the . notation. But there is an important difference.

This type of class is meant for re-use. Previously, you've seen something like this

```js
const car = {
  make: "",
  model: ""
};
const myCar = Object.create(car);
myCar.make = "Citroen";
myCar.model = "Berlingo";
```

Our new class syntax makes re-use a bit different

```js
class Car {
    constructor(){
        this.make = "Citroen";
        this.model = "Berlingo";
        this.color: "Blue";
        this.fuelType = "Diesel";
    }
}
const myCar = new Car();
myCar.make="Ferrari";
...
```

## Methods

Notice the `constructor` thingy? That's a method. It's just like a function, but when functions are tied to a class, we call it a method.

The `constructor` method is special. It's automatically called when we create a new "instance", using the `new` keyword. Try this in the console:

```js
class Student {
  constructor() {
    console.log("This student is sleepy");
  }
}
const me = new Student();
```

What happened? It `console.log`'ed "This student is sleepy", because the `constructor` method was called for us.

## `this` part #1

Classes have a special keyword referring to "this instance of the class"

Let's re-write out previous class:

```js
class Student {
  constructor() {
    this.status = "angry";
    console.log(`This student is ${this.status}`);
  }
}
const me = new Student();
```

If you try this out in the console, you probably get an error saying the the class has already been defined, just refresh and try again.
This time the status of the student is using it's own status, by writing `this.status`. But it's still not clever enough. What if we had more than one student?

## Arguments

The `constructor` method can take arguments/parameters. We specify those when we create the class. Let's re-create the Student one more time.

```js
class Student {
  constructor(name, age, status) {
    this.name = name;
    this.age = age;
    this.status = status;
    console.log(`The student ${this.name} is feeling ${this.status}`);
  }
}
const studentA = new Student("Jonas", 40, "excited");
const studentB = new Student("Maria", 23, "sleepy");
```

If you try this one out, you'll see that it console.log's two different things. Take a few moments to play around with this one. It'll all make sense soon.

## Methods, part #2

Classes can do more, much more. Our current student cannot do anything, let's fix that, by giving it a few methods. So what can all students do?

1. Sleep
2. Study
3. Eat
4. Party

Let's re-create

```js
class Student {
  constructor(name, age, status) {
    this.name = name;
    this.age = age;
    this.status = status;
  }
  sleep() {
    console.log(`${this.name} sleeps for a while`);
  }
  study() {
    console.log(
      `${this.name} studies for a while, and is now feeling ${this.status}`
    );
  }
  eat() {
    console.log(`${this.name} eats some food`);
  }
  party() {
    console.log(
      `${this.name} parties all night and now feels ${this.age + 10} years old`
    );
  }
}
const me = new Student("Jonas", 40, "tired");
me.sleep();
me.study();
me.eat();
me.party();
```

Do you get it? We define a few methods on our student, and then, once our class is "instantiated" (`const me = new Student("Jonas", 40, "tired");`) we can call the class methods on the object.

## Arguments, part #2

Still not good enough, let's make the student a little more dynamic. Let's tell him what to eat

```js
class Student {
  constructor(name, age, status) {
    this.name = name;
    this.age = age;
    this.status = status;
  }
  eat(what) {
    console.log(`${this.name} eats some ${what}`);
  }
}
const me = new Student("Jonas", 40, "tired");
me.eat("burgers");
```

I removed most of the code so we can focus on the `eat` method. The method now accepts an argument that we can use, just like regualr functions. The methods can, of course, also return stuff. The main thing to take from this is, that

1. Class methods are bound to each instance of the class. So the `eat` method belongs to the created object
2. The methods are "scoped" to that instance. You cannot call the methods `eat`, like `eat()` without using the "instantiated" object (like `me.eat()`)
3. Variables declared in the `constructor` using `this.something` are available in all the classes methods

## Calling methods

You can call methods from other methods prety easily, by writing `this.methodName()`

```js
class Student {
  constructor(name, age, status) {
    this.name = name;
    this.age = age;
    this.status = status;
  }
  eat(what) {
    console.log(`${this.name} eats some ${what}`);
    this.sleep(); // call the sleep method
  }
  sleep() {
    console.log("zzzzzzz");
  }
}
const me = new Student("Jonas", 40, "tired"); // create a new student
me.eat("burgers"); // call the eat method
```

Almost there.

## Inheritance / extending

The final concept is a bit hard. We can take an existing class and extend it to be something else, based on the original class.

So our little student, let's say he's secretly a superhero at night. Not all students are superheroes though, only some.

Let's start small

```js
class Student {
  constructor(name) {
    this.name = name;
  }
}

class SuperHero extends Student {
  constructor(name, alias) {
    super(name);
    this.alias = alias;
  }
}
const studA = new Student("Maria");
const studB = new SuperHero("Jonas", "Lord Holle");

console.log(studA.name); // Maria
console.log(studB.name); // Jonas
console.log(studA.alias); // undefined
console.log(studB.alias); // Lord Holle
```

What happened here?
Maria is a regular student.

Jonas is a superhero (apparently) so let's take a look at him,

1. We create a new superhero:

```js
const studB = new SuperHero("Jonas", "Lord Holle");
```

2. That "invokes" the SuperHero `constructor` method
3. Inside the `constructor` we see a call to a function called `super()`
4. `super()` is a magic method that calls the "parent class's contructor", in this case Student's
5. In the call to `super()` we pass in the `name`

```js
super(name);
```

which is then passed to the Student's constructor that sets `this.name`.

Now our superhero has access to everything about the student AND everything from it's own superhero class

## Challenge

Go build a class, you can create an Animal class or something, just to get the hang of it. Suggestions

1. Give it some properties
2. Give it some methods
3. In those methods, call other methods and use the properties
4. Instantiate it a few times (`const x = new Animal(...)`) and play around with it in the console
