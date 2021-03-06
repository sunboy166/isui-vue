## Input 输入框

### 概述

基本表单组件，支持 input 和 textarea，并在原生控件基础上进行了功能扩展，可以组合使用。

```
注意：非 template/render 模式下，需使用 i-input。
```

<!--divider-->

### 基础用法 

基本用法，可以使用 `v-model` 实现数据的双向绑定。

可以直接设置 style 来改变输入框的宽度，默认 100%。

```
<template>
    <Input v-model="value" placeholder="Enter something..." style="width: 300px"></Input>
</template>
<script>
    export default {
        data () {
            return {
                value: ''
            }
        }
    }
</script>

```

<!--divider-->

### 尺寸

输入框有三种尺寸：大、默认（中）、小

通过设置`size`为`large`和`small`设置为大和小尺寸，不设置为默认（中）尺寸。

```
<template>
    <Input v-model="value1" size="large" placeholder="large size"></Input>
    <br>
    <br>
    <Input v-model="value2" placeholder="default size"></Input>
    <br>
    <br>
    <Input v-model="value3" size="small" placeholder="small size"></Input>
</template>
<script>
    export default {
        data () {
            return {
                value1: '',
                value2: '',
                value3: ''
            }
        }
    }
</script>
```

<!--divider-->

### 可清空

开启属性 `clearable` 可显示清空按钮。

```
<template>
    <Input v-model="value14" placeholder="Enter something..." clearable style="width: 200px"></Input>
</template>
<script>
    export default {
        data () {
            return {
                value14: 'Hello World'
            }
        }
    }
</script>

```

<!--divider-->

### 带Icon的输入框

通过 `icon` 属性可以在输入框右边加一个图标。

点击图标，会触发 `on-click` 事件。

```
<template>
    <Input v-model="value4" icon="ios-clock-outline" placeholder="Enter something..." style="width: 200px"></Input>
</template>
<script>
    export default {
        data () {
            return {
                value4: ''
            }
        }
    }
</script>

```

<!--divider-->

### 文本域 

通过设置属性 `type` 为 `textarea` 来使用文本域，用于多行输入。

通过设置属性 `rows` 控制文本域默认显示的行数。

```
<template>
    <Input v-model="value5" type="textarea" placeholder="Enter something..."></Input>
    <br>
    <br>
    <Input v-model="value6" type="textarea" :rows="4" placeholder="Enter something..."></Input>
</template>
<script>
    export default {
        data () {
            return {
                value5: '',
                value6: ''
            }
        }
    }
</script>

```

<!--divider-->

### 适应文本高度的文本域

设置属性 `autosize`，文本域会自动适应高度的变化。

`autosize`也可以设定为一个对象，指定最小行数和最大行数。

```
<template>
    <Input v-model="value7" type="textarea" :autosize="true" placeholder="Enter something..."></Input>
    <br>
    <br>
    <Input v-model="value8" type="textarea" :autosize="{minRows: 2,maxRows: 5}" placeholder="Enter something..."></Input>
</template>
<script>
    export default {
        data () {
            return {
                value7: '',
                value8: ''
            }
        }
    }
</script>

```

<!--divider-->

### 禁用状态

通过添加`disabled`属性可设置为不可用状态。

```
<template>
    <Input v-model="value9" disabled placeholder="Enter something..."></Input>
    <br>
    <br>
    <Input v-model="value10" disabled type="textarea" placeholder="Enter something..."></Input>
</template>
<script>
    export default {
        data () {
            return {
                value9: '',
                value10: ''
            }
        }
    }
</script>
```

<!--divider-->

### 复合型输入框 

通过前置和后置的 slot 可以实现复合型的输入框。

```
<template>
    <Input v-model="value11">
        <span slot="prepend">http://</span>
        <span slot="append">.com</span>
    </Input>
    <br>
    <Input v-model="value12">
        <Select v-model="select1" slot="prepend" style="width: 80px">
            <Option value="http">http://</Option>
            <Option value="https">https://</Option>
        </Select>
        <Select v-model="select2" slot="append" style="width: 70px">
            <Option value="com">.com</Option>
            <Option value="org">.org</Option>
            <Option value="io">.io</Option>
        </Select>
    </Input>
    <br>
    <Input v-model="value13">
        <Select v-model="select3" slot="prepend" style="width: 80px">
            <Option value="day">Day</Option>
            <Option value="month">Month</Option>
        </Select>
        <Button slot="append" icon="ios-search"></Button>
    </Input>
</template>
<script>
    export default {
        data () {
            return {
                value11: '',
                value12: '',
                value13: '',
                select1: 'http',
                select2: 'com',
                select3: 'day'
            }
        }
    }
</script>

```

<!--divider-->

### 使用

### Input props

<!--table-->

| 属性           | 说明                                       | 类型      | 默认值    |
| :----------- | :--------------------------------------- | :------ | :----- |
| type         | 输入框类型，可选值为 text、password、textarea、url、email、date | String  | text   |
| value        | 绑定的值，可使用 v-model 双向绑定                    | String  | Number |
| size         | 输入框尺寸，可选值为large、small、default或者不设置       | String  | -      |
| placeholder  | 占位文本                                     | String  | -      |
| clearable    | 是否显示清空按钮                                 | Boolean | false  |
| disabled     | 设置输入框为禁用状态                               | Boolean | false  |
| readonly     | 设置输入框为只读                                 | Boolean | false  |
| maxlength    | 最大输入长度                                   | Number  | -      |
| icon         | 输入框尾部图标，仅在 text 类型下有效                    | String  | -      |
| rows         | 文本域默认行数，仅在 textarea 类型下有效                | Number  | 2      |
| autosize     | 自适应内容高度，仅在 textarea 类型下有效，可传入对象，如 { minRows: 2, maxRows: 6 } | Boolean | Object |
| number       | 将用户的输入转换为 Number 类型                      | Boolean | false  |
| autofocus    | 自动获取焦点                                   | Boolean | false  |
| autocomplete | 原生的自动完成功能，可选值为 off 和 on                  | String  | off    |
| element-id   | 给表单元素设置 id，详见 Form 用法。                   | String  | -      |
| spellcheck   | 原生的 spellcheck 属性                        | Boolean | false  |
| wrap         | 原生的 wrap 属性，可选值为 hard 和 soft，仅在 textarea 下生效 | String  | soft   |
<!--table-->
<!--divider-->

### Input events

<!--table-->

| 事件名         | 说明                  | 返回值   |
| :---------- | :------------------ | :---- |
| on-enter    | 按下回车键时触发            | 无     |
| on-click    | 设置 icon 属性后，点击图标时触发 | 无     |
| on-change   | 数据改变时触发             | event |
| on-focus    | 输入框聚焦时触发            | 无     |
| on-blur     | 输入框失去焦点时触发          | 无     |
| on-keyup    | 原生的 keyup 事件        | event |
| on-keydown  | 原生的 keydown 事件      | event |
| on-keypress | 原生的 keypress 事件     | event |
<!--table-->
<!--divider-->

### Input slot

<!--table-->

| 名称      | 说明                 |
| :------ | :----------------- |
| prepend | 前置内容，仅在 text 类型下有效 |
| append  | 后置内容，仅在 text 类型下有效 |
<!--table-->
<!--divider-->

### Input methods

<!--table-->

| 方法名   | 说明      | 参数   |
| :---- | :------ | :--- |
| focus | 手动聚焦输入框 | 无    |
<!--table-->
<!--divider-->
