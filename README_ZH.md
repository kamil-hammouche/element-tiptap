<p align="center"><a href="https://github.com/Leecason/element-tiptap" target="_blank" rel="noopener noreferrer"><img src="/examples/assets/logo_for_github.png?raw=true" alt="ElTiptap logo"></a></p>

<p align="center">
  <img alt="npm" src="https://img.shields.io/npm/v/element-tiptap">
  <img alt="GitHub Release Date" src="https://img.shields.io/github/release-date/Leecason/element-tiptap">
  <img alt="npm peer dependency version" src="https://img.shields.io/npm/dependency-version/element-tiptap/peer/vue?color=vue">
  <img alt="semantic-release" src="https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg">
  <img alt="GitHub" src="https://img.shields.io/github/license/Leecason/element-tiptap">
</p>

<h3 align="center">Element Tiptap Editor</h3>

一个 Vue.js 的基于 [tiptap](https://github.com/scrumpy/tiptap) 和 [element-ui](https://github.com/ElemeFE/element) 的 「所见即所得」 富文本编辑器

易上手，对开发者友好，可扩展性强，设计简洁

## 📔 选择语言

[English](./README.md) | 简体中文

## 🎄 Demo

👉[https://leecason.github.io/element-tiptap](https://leecason.github.io/element-tiptap)

👾[Code Sandbox](https://codesandbox.io/s/element-tiptap-bwlnj)

## ✨ 特色

- 🎨使用 [element-ui](https://github.com/ElemeFE/element) 组件
- 💅许多开箱即用的 [extension](https://github.com/Leecason/element-tiptap#extensions) (欢迎提交 issue 为新的 feature 留下建议👏)
- 🔖支持 markdown 语法
- 📘TypeScript 支持
- 🌐 支持 i18n(`en`, `zh`, `pl`, `ru`, `de`, `ko`, `es`, `zh_tw`, `fr`, `pt_br`, `nl`, `he`). 欢迎贡献更多的语言
- 🎈 可用的 `events`: `init`, `transaction`, `focus`, `blur`, `paste`, `drop`, `update`
- 🍀 高度自定义, 你可以自定义 extension 和它对应的菜单按钮视图
- 💻 也可以通过直接控制编辑器的行为来定制编辑器。

## 📦 安装

### 通过 NPM

```shell
yarn add element-tiptap
```

或者

```shell
npm install --save element-tiptap
```

#### 安装插件

```js
import Vue from 'vue';
import ElementUI from 'element-ui';
import { ElementTiptapPlugin } from 'element-tiptap';
// 引入 ElementUI 样式
import 'element-ui/lib/theme-chalk/index.css';
// import element-tiptap 样式
import 'element-tiptap/lib/index.css';

// 安装 ElementUI 插件
Vue.use(ElementUI);
// 安装 element-tiptap 插件
Vue.use(ElementTiptapPlugin, { /* 插件配置项 */ });
// 现在你已经在全局注册了 `el-tiptap` 组件。
```

默认插件配置项:

```js
{
  lang: "en", // 见 i18n
  spellcheck: true, // 可被 editor 同名 prop 重写
}
```

_或者_

#### 局部引入

```vue
<template>
  <div>
    <el-tiptap ...><el-tiptap>
  </div>
</template>

<script>
import { ElementTiptap } from 'element-tiptap';

export default {
  components: {
    'el-tiptap': ElementTiptap,
  },
};
</script>
```

## 🌐 国际化

你可以在安装插件的时候声明

```js
Vue.use(ElementTiptapPlugin, {
  lang: 'zh',
});
```

可用的语言:

- `en`(默认)
- `zh`
- `pl` by @FurtakM
- `ru` by @baitkul
- `de` by @Thesicstar
- `ko` by @Hotbrains
- `es` by @koas
- `zh_tw` by @eric0324
- `fr` by @LPABelgium
- `pt_br` by @valterleonardo
- `nl` by @Arne-Jan
- `he` by @shovalPMS

欢迎贡献更多的语言.

## 🚀 用法

```vue
<template>
  <div>
    <el-tiptap
      v-model="content"
      :extensions="extensions"
    />
  </div>
</template>

<script>
import {
  // 需要的 extensions
  Doc,
  Text,
  Paragraph,
  Heading,
  Bold,
  Underline,
  Italic,
  Strike,
  ListItem,
  BulletList,
  OrderedList,
} from 'element-tiptap';

export default {
  data () {
    // 编辑器的 extensions
    // 它们将会按照你声明的顺序被添加到菜单栏和气泡菜单中
    return {
      extensions: [
        new Doc(),
        new Text(),
        new Paragraph(),
        new Heading({ level: 5 }),
        new Bold({ bubble: true }), // 在气泡菜单中渲染菜单按钮
        new Underline({ bubble: true, menubar: false }), // 在气泡菜单而不在菜单栏中渲染菜单按钮
        new Italic(),
        new Strike(),
        new ListItem(),
        new BulletList(),
        new OrderedList(),
      ],
      // 编辑器的内容
      content: `
        <h1>Heading</h1>
        <p>This Editor is awesome!</p>
      `,
    };
  },
},
</script>
```

## 📔 Props

### 扩展 extensions

类型: `Array`

你可以只使用需要的 extension，对应的菜单按钮将会按照你声明的顺序被添加。

所有可用的 extensions:
- `Doc`
- `Text`
- `Paragraph`
- `Heading`
- `Bold`
- `Italic`
- `Strike`
- `Underline`
- `Link`
- `Image`
- `Iframe`
- `CodeBlock`
- `Blockquote`
- `ListItem`
- `BulletList` (与 `ListItem` 一起使用)
- `OrderedList` (与 `ListItem`一起使用)
- `TodoItem`
- `TodoList` (与 `TodoItem` 一起使用)
- `TextAlign`
- `Indent`
- `LineHeight`
- `HorizontalRule`
- `HardBreak`
- `TrailingNode`
- `History`
- `Table` (与 `TableHeader`, `TableCell`, `TableRow` 一起使用)
- `TableHeader`
- `TableCell`
- `TableRow`
- `FormatClear`
- `TextColor`
- `TextHighlight`
- `Preview`
- `Print`
- `Fullscreen`
- `SelectAll`
- `FontType`
- `FontSize`
- `CodeView` (🆕)

[查看](https://github.com/Leecason/element-tiptap/issues/107)所有 extensions 的文档

你可以自定义菜单按钮的渲染视图

1) 创建你自己的 extension.

```js
// 你的 extension 文件
import { Bold } from 'element-tiptap';

export default class CustomBold extends Bold {
  menuBtnView (editorContext) {
    // editorContext 包含了一些对你有用的属性，例如 isActive, commands 等
    // 更详细的文档请查看此 https://github.com/scrumpy/tiptap#editormenubar
    // ElementTiptap 将 editor 实例也添加到了其中
    return {
      component: CustomButton, // 你的组件
      componentProps: { // 会通过 v-bind 绑定到你的组件
        ...
      },
      componentEvents: { // 会通过 v-on 绑定到你的组件
        ...
      },
    },
  }
}
```

2) 在组件中使用自定义 extension
```vue
<template>
  <el-tiptap :extensions="extensions" />
</template>

<script>
import CustomBold from '...'; // 引入你的 extension

export default {
  ...
  data () {
    return {
      extensions: [
        ...
        new CustomBold(),
      ],
    };
  },
};
</script>
```

这是一个是如何自定义 extension 菜单按钮的[示例](https://github.com/Leecason/element-tiptap/issues/10#issuecomment-600979545)(一个 extension 可对应多个菜单按钮)

### editorProperties

类型: `Object`

默认值: `{}`

Tiptap `Editor` 属性（将作为参数传入 constructor）

[这里](https://github.com/scrumpy/tiptap#editor-properties)可以查看所有的属性

[`editorProps`](https://prosemirror.net/docs/ref/#view.EditorProps) 是该列表中一个强大的属性，你可以使用这个属性直接控制编辑器的行为，为自己定制编辑器。

❗一些不可用的属性❗(因为它们已经在这个包中被使用了):

- `content`
- `editable`
- `useBuiltInExtensions`
- `extensions`
- `onInit`
- `OnFocus`
- `onBlur`
- `onUpdate`

### 占位符 placeholder

类型: `string`

默认值: `''`

当编辑器没有内容的时候，将会显示 placeholder。

```html
<el-tiptap
  placeholder="Write something …"
/>
```

### 内容 content

类型: `string`

默认值: `''`

编辑器的内容

```html
<el-tiptap
  :content="content"
  @onUpdate="onEditorUpdate"
/>
```

或者使用 `'v-model'`

```html
<el-tiptap
  v-model="content"
/>
```

### 输出 output

类型: `string`

默认值: `'html'`

可被定义为 `'html'`(默认) 或者 `'json'`.

```html
<el-tiptap
  output="json"
/>
```

进一步了解: [prosemirror 数据结构](https://prosemirror.net/docs/guide/#doc)

### readonly

类型: `boolean`

默认值: `false`

```html
<el-tiptap
  :readonly="true"
/>
```

当 `readonly` 为 `true`, 编辑器不可编辑。

### spellcheck

类型: `boolean`

默认值: 插件 `spellcheck` 配置项的值

```html
<el-tiptap
  :spellcheck="true"
>
</el-tiptap>
```

编辑器内容是否开启拼写检查。

### width, height

类型: `string | number`

带单位的字符串值，无单位的值会将 **`px`** 作为单位:

```html
<el-tiptap
  :width="700"
  height="100%"
>
</el-tiptap>
```

上例会被转换为:

```css
width: 700px;
height: 100%;
```

### showMenubar

类型: `boolean`

默认值: `true`

是否显示 menubar

### charCounterCount

类型: `boolean`

默认值: `true`

是否显示字数统计

### tooltip

类型: `boolean`

默认值: `true`

鼠标移到按钮上时是否显示 tooltip

### lang

类型: `string`

默认值: 插件 `lang` 选项的值

```html
<el-tiptap
  lang="zh"
>
</el-tiptap>
```

指定编辑器国际化语言

## 👽 事件 Events

### Init

```vue
<template>
  <el-tiptap
    @onInit="onInit"
  />
</template>

<script>
export default {
  ...
  methods: {
    /*
     * tiptap editor 实例
     * 阅读 https://tiptap.scrumpy.io/docs/guide/editor.html
    */
    onInit ({ editor }) {

    },
  },
},
</script>
```

### Transaction, Focus, Blur, Paste, Drop

用法与 `init` 相同

## ⚗️ 插槽

### 菜单栏 menubar

你可以自定义菜单栏并且可以通过作用域插槽获取到一些属性。

属性：[https://github.com/scrumpy/tiptap#editormenubar](https://github.com/scrumpy/tiptap#editormenubar)

```html
<el-tiptap
  v-model="content"
  :extensions="extensions"
>
  <!-- Vue 在 2.6.0 中，为具名插槽和作用域插槽引入了一个新的统一的语法
  https://cn.vuejs.org/v2/guide/components-slots.html -->
  <template #menubar="{ commands, isActive }">
    <!--渲染自定义菜单按钮-->
    <custom-button
      :class="{ 'is-active': isActive.bold() }"
      @click="commands.bold"
    >
      Bold
    </custom-button>
  </template>
</el-tiptap>
```

### 气泡菜单 menububble

与自定义菜单栏相同的方式来自定义气泡菜单。

属性: [https://github.com/scrumpy/tiptap#editormenububble](https://github.com/scrumpy/tiptap#editormenububble)

```html
<el-tiptap
  v-model="content"
  :extensions="extensions"
>
  <template #menububble="{ commands, isActive }">
    <custom-button
      :class="{ 'is-active': isActive.bold() }"
      @click="commands.bold"
    >
      Bold
    </custom-button>
  </template>
</el-tiptap>
```

### 底部 footer

编辑器的底部，在编辑器内容的后面

## 🏗 贡献代码

详细信息见 [CONTRIBUTING](CONTRIBUTING.md)

## 📝 更新日志

[更新日志](https://github.com/Leecason/element-tiptap/blob/master/CHANGELOG.md)

## 📄 许可证

[MIT](https://github.com/Leecason/element-tiptap/blob/master/LICENSE)

## 💝 Buy Me A Coffee

看到这么多人喜欢这个项目我非常开心，有了你们的支持我会做的更好。

<p>
  <img alt="reward" src="/public/wechat_reward_qrcode.jpg?raw=true" width="300">
  <a href="https://www.buymeacoffee.com/leecason" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-blue.png" alt="Buy Me A Coffee" style="height: 51px !important;width: 217px !important;" ></a>
</p>
