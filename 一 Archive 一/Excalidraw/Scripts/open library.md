/*
```js 
*/
(async function () {
  try {
    // Access the Excalidraw API
    const excalidrawAPI = ea.targetView.excalidrawAPI;

    if (excalidrawAPI && typeof excalidrawAPI.updateScene === "function") {
      // Get the current state of the sidebar
      const currentAppState = excalidrawAPI.getAppState();

      // Check if the library tab is already open
      const isLibraryOpen = currentAppState?.openSidebar?.tab === "library";

      if (isLibraryOpen) {
        // Close the library tab if it is already open
        excalidrawAPI.updateScene({
          appState: {
            openSidebar: {
              name: "undefined",
              tab: "undefined", // This will close the tab
            },
          },
        });
      } else {
        // Open the library tab if it is not already open
        excalidrawAPI.updateScene({
          appState: {
            openSidebar: {
              name: "default",
              tab: "library", // This will open the library tab
            },
          },
        });
      }
    }
  } catch (error) {
    console.error("Error while toggling the Library tab:", error);
  }
})();










