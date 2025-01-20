/*
```javascript
*/
const newStrokeWidth = 0.5; // Set this to the desired stroke width

// Update the pen's stroke width
ea.updateScene({
  appState: {
    currentItemStrokeWidth: newStrokeWidth,
  },
});
console.log(`Pen stroke width set to ${fixedStrokeWidth}`);
