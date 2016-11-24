# Wonder.js引擎介绍

标签（空格分隔）： Wonder.js WebGL

---

## 示例
下面的代码显示一个旋转的立方体:
```js
<script>
    window.onload = function () {
        //set full screen and init engine
        wd.Main.setConfig({
            screenSize: wd.ScreenSize.FULL
        }).init();

        initSample();

        function initSample() {
            var director = wd.Director.getInstance();

            director.scene.addChild(createBox());
            director.scene.addChild(createCamera());

            director.start();
        }

        function createBox() {
            var material = wd.BasicMaterial.create();
            material.color = wd.Color.create("rgb(1.0,0.0,1.0)");

            var geometry = wd.BoxGeometry.create();
            geometry.material = material;
            geometry.width = 5;
            geometry.height = 5;
            geometry.depth = 5;

            var gameObject = wd.GameObject.create();
            gameObject.addComponent(geometry);
            gameObject.addComponent(wd.MeshRenderer.create());

            var action = wd.RepeatForever.create(wd.CallFunc.create(function () {
                gameObject.transform.rotate(0, 1, 0);
            }));

            gameObject.addComponent(action);

            return gameObject;
        }

        function createCamera() {
            var camera = wd.GameObject.create(),
                view = wd.Director.getInstance().view,
                cameraComponent = wd.PerspectiveCamera.create();

            cameraComponent.fovy = 60;
            cameraComponent.aspect = view.width / view.height;
            cameraComponent.near = 0.1;
            cameraComponent.far = 100;

            var controller = wd.BasicCameraController.create(cameraComponent);
            camera.addComponent(controller);

            camera.transform.translate(wd.Vector3.create(0, 0, 30));

            return camera;
        }
    };
</script>
```

## 设计比较
- Component
use components to assemble game object.

- Functional Reactive Programming
use Wonder-FRP library to handle async operation in frp way.

- Code Contract
use contract to improve code quality and help debug.

- Event Driven
use event system to bind dom/custom event or to implement observer design pattern in frp way.

- Composable Shader
use shader libs to assemble glsl code.


## 测试
完整的单元测试，覆盖率达93%

有渲染测试



## Feature
- Skybox
- Texture
  - Canvas Texture
  - Video Texture
  - Compressed Texture(DDS)
  - Cubemap Texture
- Procedural
  - Procedural Texture
- Light
  - Direction,Point Light
  - Diffuse Map,Specular Map,Emission Map,Light Map
  - Normal Map
  - Mirror
  - Reflection,Refraction,Fresnel
- Shadow
  - Direction,Point Light ShadowMap
- Billboard
- Event System
  - EventTriggerDetector
- Picking
  - RayCast Picking
- Collider
  - BoxCollider,SphereCollider,AABBShape,SphereShape
- Physics
  - RigidBody,Collision,Constraint,Compound
- Animation
  - Morph
  - Articulated
- Camera
  - Perspective,Orthographic Camera
  - Arcball Control
  - Fly Control
- UI
    - ThreeD UI
      - Bitmap Font
      - Solid Line, Dash Line
      - Arrow
    - TwoD UI
      - Ttf Font, Bitmap Font
      - ProgressBar
      - Image
      - Button
- Script
  - User Script
  - Event Script
- Shader
  - Custom Shader
- Optimize
    - LOD
      - Geometry LOD
      - GameObject LOD
    - Space Partition
      - Octree
    - VAO
    - Batch Draw
      - Instance
      - Render Queue Sort By RenderGroup,RenderPriority,Shader,Texture,VBO
      - Merge GameObject
- Outdoor
    - Grass
      - Grass Texture
      - Grass Instance
    - Water
    - Terrain
      - HeightMap
      - Layer Texture, Mix Texture, Bump Texture



## 工具
- Loader
support load .gltf

- Importer
support .fbx,.obj,.md2,.gltf

- terrain height map generator


## 性能(每帧渲染时间)
### 1000 boxes
wonder: 14ms
threejs: 8ms

### 1000 one direction + one point lights boxes
wonder: 24ms
threejs: 13ms


### 3000 instance monkey models
wonder: 30ms
threejs: 25ms



## Demo演示
- loading
- city
- outdoor
- race
