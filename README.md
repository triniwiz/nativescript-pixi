# nativescript-pixi

[![npm](https://img.shields.io/npm/v/nativescript-pixi.svg)](https://www.npmjs.com/package/nativescript-pixi)
[![npm](https://img.shields.io/npm/dt/nativescript-pixi.svg?label=npm%20downloads)](https://www.npmjs.com/package/nativescript-pixi)
[![Build Status](https://travis-ci.org/triniwiz/nativescript-pixi.svg?branch=master)](https://travis-ci.org/triniwiz/nativescript-pixi)

## Installation

```bash
npm i three nativescript-pixi
```

## Usage

```xml
<GridLayout width="100%" height="100%">
         <canvas:TNSCanvas width="100%" height="100%" id="canvas" ready="onReady"/>
</GridLayout>
```

```typescript
import * as PIXI from "pixi.js";
import { TNSPIXIApplication } from "nativescript-pixi";
// Create the Application by passing the canvas view object to it
 function onReady(args) {
   const canvas = args.object;
   const app = new TNSPIXIApplication({
           canvas,
           backgroundColor: 0x1099bb,
       });
       app.loader.add("bg_grass", "~/assets/images/bg_grass.jpg").load(build);
   
       function build() {
           // Create a new texture
           const texture = app.loader.resources.bg_grass.texture;
   
           // Create the simple plane
           const verticesX = 10;
           const verticesY = 10;
           const plane = new PIXI.SimplePlane(texture, verticesX, verticesY);
   
           plane.x = 100;
           plane.y = 100;
   
           app.stage.addChild(plane);
   
           // Get the buffer for vertice positions.
           const buffer = plane.geometry.getBuffer("aVertexPosition") as any;
   
           // Listen for animate update
           app.ticker.add((delta) => {
               // Randomize the vertice positions a bit to create movement.
               for (let i = 0; i < buffer.data.length; i++) {
                   buffer.data[i] += Math.random() - 0.5;
               }
               buffer.update();
           });
       }
}
```

## E.G Output
| IOS                                     | Android                                      |
| --------------------------------------- | -------------------------------------------- |
| ![ios](ss/ss_ios.gif?raw=true)) | ![android](ss/ss_android.gif?raw=true)) |


## E.G Output




## License

Apache License Version 2.0, January 2004
