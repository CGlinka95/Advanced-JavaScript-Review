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

```javascript
// Source https://github.com/HackerNews/API#items
const STORY_URL = "https://hacker-news.firebaseio.com/v0/item/8863.json"
fetch(STORY_URL)
    .then((response)=> {
        return response.json()
    }).then((storyObject)=> {
        console.log(storyObject.title)
        console.log(storyObject.url)
    })

// Written as an async function
const getStory = async ()=> {
    let response = await fetch(STORY_URL)
    let storyObject = await response.json()
    console.log(storyObject.title)
    console.log(storyObject.url)
}
getStory()
```

# Custom Promises Review

```javascript
const completeHomework = (didDoHomework)=> {
    return new Promise((resolve, reject)=> {
        if(didDoHomework) {
            //  It takes us 3 seconds to do it
            setTimeout(()=> {
                resolve("You can go out");
            }, 3000);
        } else {
            // If we didn't do our homework, we'll study
            reject("You need to study");
        }
    });
}

console.log("Can you go out with friends on Monday?")
completeHomework(true).then((result)=> {
    console.log(result);
});
// This is a positive result, so we can go out
// NOTE: We used '.then()' to process positive results

console.log("Can you go out with friends on Tuesday?")
comepleteHomework(false).catch((result)=> {
    console.log(result);
});
// This is a negative promise result, so we cannot go out :(
// NOTE: We used '.catch()' to process negative results (catches errors)
```

# Async and Await Review

```javascript
let randomDogURL = "https://dog.ceo/api/breeds/image/random";

const getRandomDogPicture = async ()=> {
    // We await the response of fetch
    let response = await fetch(randomDogURL);
    // We use await to parse the body
    let json_data = await response.json();

    //Take a look at the object
    console.log(json_data);

    return json_data.message;
}

// Call the async function in an IIFEso you can use await
(async function() {
    let picture = await getRandomDogPicture();
    document.querySelector("img").src = picture;
})();
```
