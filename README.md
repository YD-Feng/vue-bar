# vue-bar

Vue 模拟滚动条自定义指令拓展<br><br>
原版gitHub：https://github.com/DominikSerafin/vuebar<br>
本版作者：YD-Feng<br>
主要调整：注释本土化，修复了没生成模拟滚动条时，拖动内容会导致隐藏的原生滚动条显示出来的bug<br>
注意：此指令只能模拟垂直滚动条，overflow-x 会被强制置为 hidden<br>
未来计划：补全水平模拟滚动条功能<br>

<br /><br /><br />

# 使用说明
引入文件
```
<style src="vue-bar.css"></style>
<script src="vue-bar.js"></script>
```
或者通过 require，import 引入(具体引用路径根据你实际存放路径决定)
```
import './vue-bar.css';
import VueBar from './vue-bar.js';
```
<br />

成功引入后，通过 Vue.use 方法引入指令
```
import VueBar from './vue-bar.js';
Vue.use(VueBar);
```
<br />

然后在模版元素里就可以使用 v-bar 指令了
```
<div v-bar>
  <div>
    <!-- 滚动内容 -->
  </div>
  <!-- 模拟滚动条元素会插入到这个位置 -->
</div>
```
<br />

v-bar 指令支持传入一个 config 对象
```
<div v-bar="{'preventParentScroll': true, scrollThrottle: 30}">
  <div>
    <!-- 滚动内容 -->
  </div>
  <!-- 模拟滚动条元素会插入到这个位置 -->
</div>
```
<br />

config 对象各个属性的默认值及其说明
```
config = {
    unSelectableBody: true, //当你拖动模拟滚动条的时候，禁止选中 body 标签内的内容
    overrideFloatingScrollBar: true, //是否覆盖悬浮滚动条（只有在移动设备上会出现悬浮滚动条）
    scrollingPhantomDelay: 1000, //移除拖选样式（滚动条）的延迟时间
    draggingPhantomDelay: 1000, //移除拖选样式（滚动条外壳）的延迟时间
    preventParentScroll: false, //阻止父级元素滚动
    useScrollBarPseudo: false, //使用 pseudo 样式选择器来处理原始滚动条隐藏的问题，只有 chrome 和 safari 浏览器支持
}
```
<br />