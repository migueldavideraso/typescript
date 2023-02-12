# Getting started with ts

#### types
```typescript
const message:string = 'This is a simple message'
const messages:string[] = [ message ]

interface messageInterface {
  message: string;
  to: string;
  date: Date;
  set?: (a: string) => void,
  get: () => string,
}

const compleMessage:messageInterface = {
  message: 'This is a complete message',
  to: 'Elon Musk',
  date: new Date(),
  get () {
    return `\tto: ${this.to}\n\tmessage: ${this.message}\n\tdate: ${this.date.toLocaleString()}`
  }
}

function createMessage (message: string, to: string): messageInterface {

  return {
    to,
    message,
    date: new Date(),
    get () {
	    return `\tto: ${this.to}\n\tmessage: ${this.message}\n\tdate: ${this.date.toLocaleString()}`
    },
    set (newMessage: string) {
      this.message = newMessage
    }
  }
}
```


#### Composing Types

```typescript
// Unions
type CivilStatus = 'Married' | 'Single'
const civilStatus:CivilStatus = 'Married' // 'Single
// const civilStatus:CivilStatus = 'Free Union' // Error, this option is not supported in type CivilStatus

// Generics
interface PersonKeyHandler<Type> {
  set: (a: Type) => void;
  get: () => Type;
  value: Type;
}

declare const civilStatusHandler:PersonKeyHandler<CivilStatus>

// Declare an array of strings
const ids:Array<string> = []

// Declare an array of civil status
const civilStatuses:Array<CivilStatus> = []
```

#### Enums
```typescript
enum Responses {
  error = 'Has been an error, try later',
  success = 'Action done correctly'
}
```