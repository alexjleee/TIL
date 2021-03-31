# Interfaces

> The **interfaces** contain the _blueprint_ of an object. A class or a function can implement an interface.

## Class Implementing An Interface

This enforces a class to meet a particular contract.

```typescript
interface Shape {
  getArea(): number; 
  width?: number;
  height?: number;
  radius?: number;
}

// any class that are implementing the 'Shape' interface must have 'getArea()' property but other properties with '?' are optional

class Rect implements Shape {
  width: number;
  height: number;
  constructor(width: number, height: number) {
    this.width = width;
    this.height = height;
  }
  getArea() {
    return this.width * this.height;
  }
}

const rect = new Rect(2, 5);
console.log(rect.getArea()); // 10
```
