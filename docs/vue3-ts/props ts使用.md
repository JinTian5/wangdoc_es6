一、defineProps属性： 
        type: 定义数据的类型
        reqiured: 是否必须
        default: 默认值
        validator: 自定义验证
    ```javascript
    <template>
    <div class="box">
        <h1>子组件</h1>
        <h3>姓名：{{name}}</h3>
        <h3>姓名：{{age}}</h3>
    </div>
    </template>
    <script setup lang="ts">
    import { ref, defineProps } from 'vue'
    const props = defineProps(['name','age']); //方法一 通过数据方法接收

```javascript
    const props = defineProps({  //放法二 通过对象接收
        name: String,
        age: {
            type: Number,
            default: 18,
            reqiured: true,
            validator: (val) => val > 18
        },
    })
    // props.name ='qqqq'//报错，props只读
    </script>

```javascript
```javascript

import { defineComponent, PropType } from 'vue';

export default defineComponent({
  props: {
    // 基本类型的Props
    name: {
      type: String,
      required: true
    },
    age: {
      type: Number,
      default: 18
    },
    // 自定义类型的Props
    person: {
      type: Object as PropType<{ name: string, age: number }>,
      required: true
    },
    // 数组类型的Props
    hobbies: {
      type: Array as PropType<string[]>,
      default: () => []
    }
  },
  // ...
});

