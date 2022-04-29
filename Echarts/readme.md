# Vue自定义组件封装：

  **versions :** **0.1.0** 

> 现已经封装Echarts,可以直接引用组件，仅需操作图表的高度和宽度及options即可实现一个Echarts图

## 1. 开始使用

1. 下载或复制： 直接下载代码，或者进入组件包直接复制  

> `注意： 一个组件包包含所有组件所需的文件，务必全部下载或复制，文件名务必保持一致`

2. 安装：将下载下来的包或者复制下来的包放在vue项目中的components文件夹中即可
3. 引入： 在使用的页面引入即可

```vue
//引入组件
import Echarts from "../components/Echarts/Echarts.vue"
//引用options
import {options1, options2} from '../components/Echarts/options'
```

> `注意：组件引入后需要配置一些vue组件必备参数`

4. 配置：

```vue
export default {
    name: 'Charts',
    components: {
		//注册的组件名称（自定义）
        Echarts
    },
    data(){
        return{
			//echarts 必备参数options
            options1:options1,
            options2:options2,
			//自定义的宽高
            width: '800px',
            height: '600px'
        }
    }
}
```

5. 使用

```vue
<Echarts :width="width" :height="height" :options="options1"></Echarts>
```



