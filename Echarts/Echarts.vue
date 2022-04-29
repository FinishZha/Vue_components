<template>
  <div :id="uuid" :style="stytle"></div>
</template>

<script>
import * as echarts from "echarts"
import { getUUID } from "./uuid"

export default {
  name: "Echarts", 
  props:{
    height:{
      type: String,
      default: '400px'
    },
    width: {
      type: String,
      default: '600px'
    },
    options:{
      type: Object,
      default: null
    }
  },
  data() {
    return {
      uuid: null,
      myChart:null
    };
  },
  methods: {},
  computed:{
    stytle(){
      return{
        height: this.height,
        width: this.width
      }
    }
  },
  watch:{
    width() {
      if(this.myChart){
        this.myChart.resize({
          animation:{
            duration: 300
          }
        })
      }
    },
    height(){
      if(this.myChart){
        this.myChart.resize({
          animation:{
            duration:300
          }
        })
      }
    },
   options(){
     if(this.myChart) {
       this.myChart.setOption(this.options)
     }
   }
  },
  created(){
    //动态生成uuid
    this.uuid = getUUID(8,16)
  },
  mounted() {
    //官方流程
    const myChart = echarts.init(document.getElementById(this.uuid));
    
    // 应用配置项
     myChart.setOption(this.options);
  },
};
</script>

<style>