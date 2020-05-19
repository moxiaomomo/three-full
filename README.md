## three-full
A quick way to gather almost example modules of threejs

## Processing steps (tested on r108)

- 1. Using shell to list all modules to a custom file

```shell
cd node_modules/three
egrep "export (const|function|class|interface)" examples/* -nr | grep "\.d\.ts" | egrep -v "\/GLTFLoader|\/VTKLoader|\/XLoader|\/TessellateModifier|\/Water2|\/BokehShader2|\/TextureCubeUVNode|\/TextureCubeNode|\/SubSlot" | awk -F: '{print $1}' | sed s/\.d\.ts//g | sort | uniq | awk '{print "export * from '\''three/" $1 "'\'';"}' > /yourpath/somefile.ts
```

- 2. Add the remaining modules to /yourpath/somefile.ts

```javascript
export { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader';
export { Water as Water2 } from 'three/examples/jsm/objects/Water2';
export { BokehShader as BokehShader2 } from 'three/examples/jsm/shaders/BokehShader2';
```
```javascript
// The following modules can be imported separately manually
// import { VRMLLoader as XLoader } from 'three/examples/jsm/loaders/XLoader';
// import { VRMLLoader as VTKLoader } from 'three/examples/jsm/loaders/VTKLoader';
// import { SubdivisionModifier as TessellateModifier } from 'three/examples/jsm/modifiers/TessellateModifier';
```

- 3. other discussions

https://github.com/mrdoob/three.js/issues/17409


## Processing steps (tested on r116)

- 1. Using shell to list all modules to a custom file

```shell
cd node_modules/three
egrep "export (const|function|class|interface)" examples/* -nr | grep "\.d\.ts" | egrep -v "\/GLTFLoader|\/VTKLoader|\/XLoader|\/TessellateModifier|\/Water2|\/BokehShader2|\/TextureCubeUVNode|\/TextureCubeNode|\/SubSlot" | awk -F: '{print $1}' | sed s/\.d\.ts//g | sort | uniq | awk '{print "export * from '\''three/" $1 "'\'';"}' > /yourpath/somefile.ts
egrep "export (const|function|class|interface)" srx/extras/* -nr | grep "\.d\.ts" | awk -F: '{print $1}' | sed s/\.d\.ts//g | sort | uniq | awk '{print "export * from '\''three/" $1 "'\'';"}' >> /yourpath/somefile.ts
```

- 2. Add the remaining modules to /yourpath/somefile.ts

```javascript
export { GLTFLoader, GLTF } from 'three/examples/jsm/loaders/GLTFLoader';
export { Water as Water2 } from 'three/examples/jsm/objects/Water2';
export { BokehShader as BokehShader2 } from 'three/examples/jsm/shaders/BokehShader2';
```
