# Unity GameDepot Bridge

## Introduction
This guide provides step-by-step instructions for integrating GameDepot into your Unity project. By following these steps, you'll be able to seamlessly set up and use GameDepot in your project.

## Setup Guide

### Step 1: Download source code

### Step 2: Setup the GameDepot Bridge
1. Begin by copying the "Assets/GameDepot" folder into your Unity project "Assets" directory.
2. Open your start scene in Unity.
3. Drag and drop prefab "GameDepotBridge" from the "Assets/GameDepot/Prefabs" to the first scene in your project.
4. Integrate GameDepot with your game using public methods from the "GameDepotBridge".

### Step 3: Setting Up Your WebGL Template
- If you're using the provided custom WebGL template:
    - Simply copy and paste "WebGLTemplate" folder into your "Assets". And that's all, skip next steps.
- If you are using your own custom WebGL template:
    - Copy the [`GameDepotBridge.js`](https://github.com/ton-play/playdeck-unity-integration/blob/master/Assets/WebGLTemplates/CustomTemplate/playDeckBridge.js) file to the same directory as your `index.html` file.

### (Additional) Step 4: Modifying index.html of custom WebGL template
1. **Adding the GameDepot Script:**
    - Open your `index.html` file.
    - Inside the `<head></head>` tags, add the following line:
      ```html
      <script src="GameDepotBridge.js"></script>
      ```
2. **Updating Unity Loading Code:**
    - Find the section in your `index.html` where Unity is loading (creating the Unity instance).
    - Update it using the following code example:
      ```javascript
      const GameDepotBridgeInstance = GameDepotBridge();
      createUnityInstance(canvas, config, (progress) => {
          GameDepotBridgeInstance?.setLoadingProgress(progress * 100)
      }).then(unityInstance => {
          GameDepotBridgeInstance?.init(unityInstance);
      });
      ```

### Step 5: Testing
- After making these changes, save your `index.html` file.
- Return to Unity, make and deploy build, test your project to ensure that GameDepot is integrated and functioning correctly.

## Additional Notes
- This guide assumes a basic familiarity with Unity and web development.
- If you encounter any difficulties, you may contact us for additional help.
