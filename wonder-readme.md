<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#sec-1">1. Wonder.js</a></li>
<li><a href="#sec-2">2. Goal</a></li>
<li><a href="#sec-3">3. Document</a></li>
<li><a href="#sec-4">4. Design</a></li>
<li><a href="#sec-5">5. Contributing</a></li>
<li><a href="#sec-6">6. Feature</a></li>
<li><a href="#sec-7">7. Usage</a></li>
<li><a href="#sec-8">8. How to build</a></li>
<li><a href="#sec-9">9. How to test</a></li>
<li><a href="#sec-10">10. License</a></li>
</ul>
</div>
</div>

# Wonder.js<a id="sec-1" name="sec-1"></a>

Wonder.js is a 3D Javascript Game Engine.

# Goal<a id="sec-2" name="sec-2"></a>

To build a elegant, beautiful 3D game engine with full functions.

# Document<a id="sec-3" name="sec-3"></a>

Please learn samples in examples/samples/ to get more info.

# Design<a id="sec-4" name="sec-4"></a>

-   Component
    use components to assemble game object.
-   Functional Reactive Programming
    use Wonder-FRP library to handle async operation in frp way.
-   Design by Contract
    use dbc to improve code quality, help to debug.
-   Event Driven
    use event system to bind dom/custom event or to implement observer design pattern in frp way.
-   Composable Shader
    use shader libs to assemble glsl code.

# Contributing<a id="sec-5" name="sec-5"></a>

Join us, We can create the 3D world together!

# Feature<a id="sec-6" name="sec-6"></a>

-   Animation
    -   Morph
-   Camera
    -   Perspective,Orthographic Camera
    -   Arcball Control
    -   Fly Control
-   Light
    -   Direction,Point Light
    -   Diffuse Map
    -   Specular Map
    -   Normal Map
    -   Mirror
    -   Reflection,Refraction,Fresnel
-   Script
    -   User Script
-   Shader
    -   Custom Shader
-   Shadow
    -   Direction,Point Light ShadowMap
-   Skybox
-   Texture
    -   Canvas Texture
    -   Video Texture
    -   Compressed Texture(DDS)
    -   Cubemap Texture
-   Converter
    -   OBJ Converter
    -   MD2 Converter

# Usage<a id="sec-7" name="sec-7"></a>

Include library in your html:

    <script src="js/wd.min.js"></script>

Here shows a spinning cube sample:

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

# How to build<a id="sec-8" name="sec-8"></a>

You can install engine by bower:

    bower install wd

For node.js project, you can install engine by npm:

    npm install wd

You can build engine by gulp task:

    gulp build

# How to test<a id="sec-9" name="sec-9"></a>

-   unit test
    Wonder has complete unit test, you can run the unit test by gulp task:

    gulp test

-   debug
    You can first include wd.innerLib.js file, then include wd.debug.js file in your html, then you can debug in engine ts
    file:

    <script src="js/wd.innerLib.js"></script>
    <script src="js/wd.debug.js"></script>

# License<a id="sec-10" name="sec-10"></a>

MIT Licence