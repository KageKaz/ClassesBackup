/*
```js*/

// Define the script to capture and compare Excalidraw app state

  

let differences = {};

// Function to deep compare two objects and log differences

function logObjectDifferences(obj1, obj2, path = "") {

    Object.keys({...obj1, ...obj2}).forEach(key => {

        const fullPath = path ? `${path}.${key}` : key;

        if (obj1?.[key] !== obj2?.[key]) {

            if (typeof obj1?.[key] === "object" && typeof obj2?.[key] === "object") {

                logObjectDifferences(obj1?.[key], obj2?.[key], fullPath);

            } else {

              differences[fullPath] = {oldValue: obj1?.[key], newValue: obj2?.[key]};

            }

        }

    });

}

  
  

// Retrieve the current Excalidraw app state

const currentState = ea.getExcalidrawAPI().getAppState();

  

// Check if there's a previous state stored in ExcalidrawAppStateCache

if (window.ExcalidrawAppStateCache) {

    console.log("Comparing to previous app state...");

    differences = {};

    logObjectDifferences(window.ExcalidrawAppStateCache, currentState);

    console.log("Differences between appState are ", differences);

} else {

    console.log("No previous state found. This is the initial capture.");

}

  

// Update the ExcalidrawAppStateCache with the current state

window.ExcalidrawAppStateCache = JSON.parse(JSON.stringify(currentState));

console.log("Current app state has been cached.");