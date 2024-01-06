# Three.js介紹
* 在網頁上製作3D的函式庫
* 基於 WebGL
* 範例：互動專輯、品牌網頁、互動MV、視覺藝術

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f9c32a944baca75169bed0ce1c1a542f)

---

## 場景與概念-3D中四大主角-
* 物件(object)：實際的物體
* 光源(light)：照亮物體
* 材質(material)：決定每個面怎麼渲染
* 攝影機(camera)：決定視角、視野跟渲染
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_071d73da2c25c2840dc5fb1f7263b146)

---
###  1. 物件
* 物件由形狀[Geometry](https://threejs.org/docs/#api/en/geometries/BoxGeometry)＋材質組成 [Material](https://hackmd.io/@0NQpKOczRQieAHcN299jug/ByFP8X_7X?type=view)
* 採取scene-child管理模式
* 把製作好的物件加入舞台[Scene](https://threejs.org/docs/#api/en/scenes/Scene)中
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_75c45d9d61d43f795350507ff58cf7a6)


---

### 2. 光源
* 點光源：控制位置、衰弱(falloff)
* 聚光燈：控制位置、光束角度、衰弱
* 平行光：DirectionalLight
* 環境光源：基礎強制光源
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d2fead04e0f630ee7bc4102cec2660bd)

---

### 3. 材質
* 不同種材質有不同表現
* 可以指定顏色、貼圖
* 重點參數： 反光(reflect)、散射(difuse)、凹凸(bump)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3fdb4dd099b6f3817ca26705f3083ee6)
//https://arnold-rendering.com/2016/04/21/material-studies-metals/

---

### 4. 攝影機與渲染
* 視野-Field-Of-View
* renderer: WebGL / Canvas / Css / SVG
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_76cfda10f64bf6109a56d75d683580db)

---
### Css Renderer

https://threejs.org/docs/#examples/renderers/CSS3DRenderer
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0282fc57ce5fafeda5a9074249023b36)

---
### 5. 3D中的滑鼠定位
* Raycast https://threejs.org/examples/?q=raycas#webgl_raycast_texture
* 物件選擇 https://threejs.org/examples/#webgl_interactive_instances_gpu
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5cceafe61069b38abc8ee27923612bb2)

### 3D模型物件
https://sketchfab.com/

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ca70f42ecf25da6bfb340b1ab728da96)
