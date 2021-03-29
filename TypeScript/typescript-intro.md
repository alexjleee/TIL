# TypeScript Intro

## What Is TypeScript

**TypeScript** is an open-source language developed by Microsoft. It is a superset of JS. It extends JS by adding _types_ and compiles to plain JS using TypeScript Compiler (TSC).

JS is dynamically typed - which means it is very easy to make errors that will only be caught at runtime. TS uses strict typing to prevent such errors.

## Setup
1. Install `typescript` globally with npm

    ```$ npm i -g typescript```

2. Write `.ts` file and compile it into `.js` file with `tsc` command

    ```$ tsc index.ts```

By installing `typescript` package you will have access to the `tsc` command, which will run TypeScript Compiler. TypeScript file (`.ts`) on its own, can't run anywhere. It needs to be compiled into JS file (`.js`). 

### How To Change Compiler Options
1. Create `tsconfig.json`

    ```$ touch tsconfig.json```

2. Customise compiler options using `compilerOptions`

    ```json
      {
        "compilerOptions": {
          "target": "esnext", // "es3" by default
          "watch": true, // recompile the code if there are changes
        }
      }
    ```

## Strong Typing Variables

1. Assigning types implicitly 

```typescript
let name = 'Alex'; // let name: string
let age = 27; // let age: number

age = '27'; // [ts] Type "27" is not assignable to type 'number'
```

2. Assigning types explicitly

```typescript
let num: number;
let anyType: any;

num = '27'; // error
num = 27;

anyType = 'hello'; 
anyType = 2021;
```

- cf. This is unnecessary 
  ```typescript
  let num: number = 27;
  ```

## Strong Typing Objects - Interface

You can enforce the shape of an object

```typescript
interface Person {
  firstName: string;
  lastName: string;
  age: number;
}

const person1: Person = {
  firstName: 'Alex',
  lastName: 'Lee',
  isKorean: true // error
}
```

## Strong Typing Functions

```typescript
// inputs must be numbers and the returned value must be a string
function add(x: number, y:number): string {
  return (x + y).toString();
}
```

## Strong Typing Arrays

```typescript
const numArr: number[] = [];
numArr.push(0);
numArr.push('1'); // error
```

- Tuple : fixed length array where the each element has its own type

```typescript
type MyTuple = [string, number, boolean];
const tupleArr: MyTuple = [];
tupleArr.push('Alex');
tupleArr.push(27);
tupleArr.push('korean'); // err
```