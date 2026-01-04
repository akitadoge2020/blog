# Vue3+Vite兼容旧版浏览器

> 2024.06.05

## 问题描述

在一个 h5 项目中兼容旧版浏览器时，出现报错 replaceAll is not a function。

## 解决过程与方案

通过 MDN 文档发现 String.prototype.replaceAll 方法能够兼容 webview 内核最低版本是85，而我们的测试机版本是70。

![image-20260104163231466](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/202601041632497.png)

因此需要对该方法进行 Pollyfill，配置如下：

```js
import { defineConfig } from 'vite'
import legacy from '@vitejs/plugin-legacy'
export default defineConfig({
    plugin: [
        legacy({
            targets: ['chrome>=63', 'safari >= 7'],
            polyfills: ['esnext.string.replace-all'],
            modernPolyfills: ['esnext.string.replace-all']
        })
     ]
})
```



## 参考链接

- [String.prototype.replaceAll polyfill is not included · Issue #7449 · vitejs/vite (github.com)](https://github.com/vitejs/vite/issues/7449)
- [plugin-legacy doesn't work · Issue #7940 · vitejs/vite (github.com)](https://github.com/vitejs/vite/issues/7940)

附上安卓和webview版本对照表：[android - Android各系统版本预装的Chrome内核版本有统计的吗？ - SegmentFault 思否](https://segmentfault.com/q/1010000043739779)

![image-20250503133856686](https://penguinbucket.obs.cn-southwest-2.myhuaweicloud.com/img/202505031338745.png)