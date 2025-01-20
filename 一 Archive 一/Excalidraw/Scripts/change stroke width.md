ea.registerCommand({
  name: "Set Pen Stroke Width", // Name of the command that shows in the command palette
  description: "Change the pen's stroke width to a specific value", // Optional description
  perform: () => {
    const newStrokeWidth = 2; // Set this to the desired stroke width

    // Update the pen's stroke width
    ea.updateScene({
      appState: {
        currentItemStrokeWidth: newStrokeWidth,
      },
    });

    console.log(`Pen stroke width set to ${newStrokeWidth}`);
  },
});
