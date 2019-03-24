[![Build Status](https://travis-ci.org/merlosy/ngx-material-file-input.svg?branch=master)](https://travis-ci.org/merlosy/ngx-material-file-input)
[![npm](https://img.shields.io/npm/dt/ngx-material-file-input.svg)](https://www.npmjs.com/package/ngx-material-file-input)
[![](http://img.badgesize.io/https://unpkg.com/ngx-material-file-input@latest/bundles/ngx-material-file-input.umd.min.js?label=full%20size%20as%20min.js&compression=gzip&style=square&color=02adff)](https://www.npmjs.com/package/ngx-material-file-input)
[![Known Vulnerabilities](https://snyk.io/test/github/merlosy/ngx-material-file-input/badge.svg)](https://snyk.io/test/github/merlosy/ngx-material-file-input)

# material-file-input

这个项目提供 :

* `ngx-mat-file-input` 组件, 在Angular Material中使用 `mat-form-field`
* a `FileValidator` 带 `maxContentSize`, 限制文件大小
* a `ByteFormatPipe` 以人类可读的格式格式化文件大小

有关更多代码示例，请查看[演示网站](https://merlosy.github.io/ngx-material-file-input)

## 安装

```sh
npm i ngx-material-file-input
```

## API参考

```ts
import { MaterialFileInputModule } from 'ngx-material-file-input';
```

### 可选的 NGX_MAT_FILE_INPUT_CONFIG token:

更改ByteFormat管道的单位

```ts
export const config: FileInputConfig = {
  sizeUnit: 'Octet'
};

// 添加模块注入
providers: [{ provide: NGX_MAT_FILE_INPUT_CONFIG, useValue: config }];
```

### NgxMatFormField

selector: `<ngx-mat-file-input>`

implements: [MatFormFieldControl](https://material.angular.io/components/form-field/api#MatFormFieldControl)<FileInput> from Angular Material

** 附加属性 **

| Name | Description |
| - | - |
| _@Input()_ valuePlaceholder: `string` | 文件名的占位符，默认为空 |
| _@Input()_ multiple: `boolean` | 允许多个文件输入, `false` 默认情况下 |
| _@Input()_ autofilled: `boolean` | 输入当前是否处于自动填充状态。 如果控件上没有属性，则认为它是false。 |
| _@Input()_ accept: `string` | `accept`属性可以获得的任何值。 [更多关于"accept"](https://www.w3schools.com/tags/att_input_accept.asp) |
| value: `FileInput` | 表单控制值 |

### ByteFormatPipe

** 例 **

```html
<span>{{ 104857600 | byteFormat }}</span>
```

_Output:_ 100 MB

### FileValidator

| name | 描述 | 错误结构 |
| - | - | - |
| maxContentSize(value: `number`): `ValidatorFn` | 将总文件大小限制为给定值 | `{ actualSize: number, maxSize: number }` |

## 关于我

[@jereyleg](https://twitter.com/jereyleg)

&star; 表示支持 :)

## 路线图

* drop event to add files
* _ideas?_

## 感谢

* https://github.com/dherges/ng-packagr
* Jason Aden - 打包Angular库 https://www.youtube.com/watch?v=QfvwQEJVOig
