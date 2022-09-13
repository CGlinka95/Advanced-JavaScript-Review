# Advanced JavaScript Review

## Defining an Object

```javascript
let myDog = {
    name: 'Keeva',
    color: 'Black and White',
    age: 3,
    isMale: false,
    isFemale: true
};
// Accessing the name property on the myDog object uses the "." operator
console.log(myDog.name);

// Accessing the color property on the myDog object uses "[]"
console.log(myDog['color']);
```

## Using functions and 'this'

```javascript
let user = {
    name: "Chris",
    interests: ["videogames", "hockey", "coding", "roblox development"],
    isInterested(topic) {
        if (this.interests.includes(topic)) {
            console.log('${this.name} is interested in ${topic}')
        } else {
            console.log('${this.name} is not interested in ${topic}')
        }
    }
}

// Call the function
user.isInterested("hockey")
// If true: "Chris is interested in hockey"

user.isInterested("boring stuff")
// If false: "Chris is not interested in boring stuff"
```

# Node and NPM Review

- To access the javascript ecosystem, you need to access it through NPM (Node Package Manager)
- To check that you have npm installed, type 'npm -v' in to a cmd line
- To use npm in your projects, you'll need to start a project with 'npm init'
- This will create a "package.json" file 

```json
{
    "name": "nodefirst",
    "version": "1.0.0",
    "description": "our first project",
    "main": "index.js",
    "scripts": {
        "hello": "echo \"is there anybody out there? \""
    },
    "author": "chris glinka",
    "license": "ISC",
    "devDependencies": {
        "@babel/cli": "^7.7.5",
        "@babel/core": "^7.7.5",
        "@babel/preset-env": "^7.7.6"
    },
    "dependencies": {}
}
```

- The command line scripts that you have access to are under "scripts".
- "devDependencies" are packages that you have access to in your dev environment
- "dependencies" are packages that you have access to everywhere 

# ES Modules Review

```javascript
// food.js file
const FOOD_THOUGHTS = {
    'sushi': 30, // many more
}

const getFoodThoughtKeys = ()=> {
    return Object.keys(FOOD_THOUGHTS)
}

const getFoodThoughtsValues = ()=> {
    return Object.values(FOOD_THOUGHTS)
}

export {getFoodThoughtKeys, getFoodThoughtsValues}

// index.js file (in the same folder as food.js)

// How to import files locally:
import{getFoodThoughtKeys,
       getFoodThoughtsValues} from './food.js'

// Call the functions
getFoodThoughtKeys()
getFoodThoughtsValues()
```

# Fetch Review

... todo later...
