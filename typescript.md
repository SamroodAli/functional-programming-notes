# Welcome to TypeScript

[Notes](https://www.typescript-training.com/course/fundamentals-v3) from mike north's typscript fundamentals 
## Variables
### Let variables
TS can infer from the value what the type is.

```ts
let age = 6
```

Here, type of age is number.
We can assign it something else. but TS will yell at us. It will run though.

```ts
let age = 6
age = "Not a number"
```
### Const variables

```js
const age = 6
```
Here age has the literal type `6`. It can only a number that is 6. Since typescript knows const cannot point to anything else and the value it is pointing to cannot be changed.

## Functions

```ts
function add(a: number, b: number): number {
  return a + b
}
```
## Collections: [Arrays, Objects, Types]

### Object: type is the shape of the data

```ts
//declaration
let car:{
  make:string,
  model:string,
  year:number
}

// assignment
car = {
  make: "Toyota",
  model: "Corolla",
  year:   2002
}
```

#### Optional property with ?:
```ts

let car:{
  chargeVoltage?:number
}
```
#### Type guard

```ts
let user: {
  name:string,
  age:number,
  student:boolean,
  friends ?:[{name:string,age:number,student:true}]
 } = {
  name:"Samrood",
  age:24,
  student:true
}

function printUser(user:{
  name:string,
  age:number,
  student:boolean,
  friends?:[{name:string,age:number,student:true}]
 }){
  let str:string  = `${user.name}, ${user.age}, student:${user.student}`

  if (user.friends){
    str += `${user.friends[0].age.toString()}`
  }
  console.log(str)
 }


 printUser(user)

```

#### Multiple types with | (or)
```ts
let something:string | number;
something  = 10
something  ="Samrood"
```

#### Index signatures - Consistent values (dictionaries) in objects
Sometimes we have consistent  keys and consistent values

```ts
const phones = {
  home: { country: "+1", area: "211", number: "652-4515" },
  work: { country: "+1", area: "670", number: "752-5856" },
  fax: { country: "+1", area: "322", number: "525-4357" },
}
```
This can be represented as follows.

```ts
let object:{
  [k:string]: {
    [k:string]:string,
    number:number
  }
}
```
#### Preventing against keys that does not exit when indexing (allowing any keys)

```ts
let user:{
  [k:string]: {age: number} | undefined // this undefined will make sure we are type guarding against possible undefined when retrieving a key that does not exist
}
```

```ts
if(user.samrood){ // since user.samrood can be undefined, we do type guarding here.
  user.samrood.age
}
```

## Arrays.


Declaration
```ts
let array:string[] =['samrood']
let array:string[][] = [['samrood'],['leon']]
let array:{name:string}[] = [{name:"Samrood"}]
```

## Tuples
Fixed length arrays
```ts
let age:[string,number]= ['samrood','leon']
```

There is currently no enforcing on the tuple's length. So push and pop bypass length for tuples.
But pushing types not specified does show an error.
```ts
let array:[string,number] = ["Samrood",10]
array.push(10)
```

## Types of types
[Read on Mike north's typescript website](https://www.typescript-training.com/course/fundamentals-v3/05-structural-vs-nominal-types/)
