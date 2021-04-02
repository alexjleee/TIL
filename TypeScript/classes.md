# Classes

> The classes in TS is similar to the classes in JS. The main difference is that you can set types of the fields and add _private_, _public_ and _readonly_ modifiers to them.

## Fields

- Fields should have initializers or should be definitely assigned in the constructor.

1. Initializers
    ```typescript
    class Location {
      x = 0;
      y = 0;
    }
    ```
2. Initialized in the constructor
    ```typescript
    class Location {
      x: number;
      y: number;

      constructor(x: number, y: string) {
        this.x = x;
        this.y = y;
      }
    }
    ```

- Fields can have `readonly` modifier. This prevents assignments to the field outside of the constructor.
    ```typescript
    class User {
      readonly name: string;

      constructor(name: string) {
        this.name = name;
      }

      changeName() {
        this.name = 'Alex'; // error
      }
    }

    const user1 = new User('Lewis');
    user1.name = 'Alex'; // error
    ```

## Constructors

- You can add parameters with type annotations.
    ```typescript
    class Location {
      x: number;
      y: number;

      constructor(x: number, y: string) {
        this.x = x;
        this.y = y;
      }
    }
    ```

## Methods

- You can add type annotations.
    ```typescript
    class User {
      readonly name: string;

      constructor(name: string) {
        this.name = name;
      }

      greet(msg: string): string {
        return `Hello, ${this.name}. ${msg}`
      }
    }
    ```

## Access Modifiers

- The class members are `public` - accessible from everywhere - by default.
- `protected` only allows access to the member from subclasses of the class.
- `private` does NOT allow access to the member even from subclasses.

- If the access modifiers are specified, 
    ```typescript
    class User {
      name: string;
      private authCode: number;

      constructor(name: string, authCode: number) {
        this.name = name;
        this.authCode = authCode;
      }
    }
    ```
  can be written like this:
  ```typescript
    class User {
      constructor(public name: string, private authCode: number) {
        this.name = name;
        this.authCode = authCode;
      }
    }
  ```