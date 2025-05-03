# antDesignVue封装方法型组件问题

> 2025.04.18

## 问题描述

antDesignVue1.x 在方法型组件中子组件 popover 状态更新时，会触发父组件 created、mouted 重新执行，beforeDestroy、destroyed 不会重新执行。

demo地址：[CodeSandBox](https://codesandbox.io/p/sandbox/3t62w4)



## 解决过程与方案

一开始在业务层寻找问题，一直找不到问题所在，只能抽丝剥茧，创建一个尽可能剥离业务逻辑、简洁的组件来调试，最终发现跟 popover 有关的 ant 组件都会导致这个问题。到这里基本能说明是 ant-design-vue 的 bug 了，那么就查看一下有没有相关的 issue，结果发现了两条。

- [子组件操作/更新时 父组件 created/mounted 会再次被执行 · Issue #2581 · vueComponent/ant-design-vue (github.com)](https://github.com/vueComponent/ant-design-vue/issues/2581)
- [ cause duplicate execution of $root life hooks · Issue #4487 · vueComponent/ant-design-vue (github.com)](https://github.com/vueComponent/ant-design-vue/issues/4487)

按照上述两条 issue 得出两个解决方案：

1. （推荐）使用 Vue.extends 的话，需要在创建实例后，重置 constructor 为 Vue

```js
import Vue from "vue";
import TestModal from "./TestModal";

const TestModalConstructor = Vue.extend(TestModal);

export default function () {
  const instance = new TestModalConstructor();
  instance.constructor = Vue;
  instance.visible = true;

  instance.$mount();
  document.body.appendChild(instance.$el);
}

```



2. 组件创建的方式从 Vue.extends 改为 Vue 实例

```js
import Vue from "vue";
import TestModal from "./TestModal";

export default function (options) {
  const instance = new Vue({
    mounted() {
      const child = this.$children[0];
      for (const key in options) {
        child[key] = options[key];
      }
      child.visible = true;
    },
    render: (h) => h(TestModal),
  });

  instance.$mount();
  document.body.appendChild(instance.$el);
}
```

