# 协变逆变

## 协变
```ts
class Animal {
  name: string;
}

class Dog extends Animal {
  breed: string;
}

let myDog: Dog = new Dog();
let myAnimal: Animal = myDog;  // OK，因为Dog是Animal的子类型
```

```ts
type Animal = { name: string };
type Dog = Animal & { breed: string };

let dogs: Dog[] = [{ name: "Fido", breed: "Poodle" }];
let animals: Animal[] = dogs;  // OK because Dog extends Animal, Dog[] is a subtype of Animal[]

```

## 逆变

```ts
type Animal = { name: string };
type Dog = Animal & { breed: string };

let dogHandler = (dog: Dog) => { console.log(dog.breed); }
let animalHandler: (animal: Animal) => void = dogHandler;  // Error! 
```

因为如果我们传递一个 Animal (并非所有的 Animal 都是 Dog) 给 animalHandler，那么在执行 dogHandler 函数的时候，就可能会引用不存在的 breed 属性。

因此，函数的参数类型是逆变的。
