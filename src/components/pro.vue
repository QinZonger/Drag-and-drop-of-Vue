<template>
    <div class="pro">
        <div class="progressContainer">
            <div class="progress" :style="{left:widths+'%'}" ref="move"> </div>
        </div>
        <div class="listnum">
            <div v-for="(item,index) in bottom" :class="{active:index==act}" :key="index" @click="changePro(index)" class="aa">
                {{item}}
            </div>
        </div>
    </div>
</template>
<script>
    let x=0
    let px=0;
    let onDrag = false;
export default {
    name:"pro",
    data(){
       return {
        bottom:["1.0","2.0","3.0","4.0","5.0","6.0","7.0","8.0","9.0","10.0"],
        act:0,
        widths:"0"//默认的left值
       }
    },
    methods:{
       changePro (index){
            let num = 10;//背景的长度
            this.act = index;//高亮
            this.widths = num * index;//每次点击的那个长度
            //console.log(this.widths,'------w')
       },
        Move () {
           this.$refs.move.onmousedown = (e) =>{ //开始点击
              x = e.clientX;
              px = this.$refs.move.offsetLeft;
              onDrag = true;
              console.log('点击')
                window.onmousemove = (e) => { //移动
                    if (onDrag) {
                    let nx = e.clientX + px - x;
                    if (0<nx && e.clientX <485) {
                        this.$refs.move.style.left = nx + 'px'
                        console.log('移动')
                    }
                    }
                }
                window.onmouseup = () => {  //不在点击
                    if (onDrag) {
                        onDrag = false;
                        console.log('移除')
                    }
                }
           }
       }
    },
    mounted(){
        this.Move()
    }
}
</script>
<style>
.active{
    color:red;
}
div.progressContainer{
    height: 20px;
    width: 96%;
    /* border-radius: 10px; */
    background-color: #ddd;
    margin-left: 2%;
    margin-top: 5%;
    position: relative;
}
div.progress{
    background-color: #1C8DE0;
    /* border-radius: 10px; */
    width:16px;
    height:30px;
    margin: 3px;
    margin-top: -5px;
    position: absolute;
    left: 0;
    line-height: 30px;
    display: inline-block;
}
b{
    color:#fff;
    font-weight: 100;
    font-size: 12px;
    position:absolute;
    left:40%; 
 }
 .listnum{
     width: 100%;
     height: 30px;
     line-height: 30px;
     display: flex;
     margin-top: 10px;
 }
 .aa{
     width: 10%;
    margin: 0 5px;
    font-size: 14px;
 }
</style>