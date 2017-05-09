

<template>
  <div class="box">
    <a id="sss" >
    <div class="box-container" ref="i" :style="containerTransform" >
      <span class="box-container__text" :style="textTransform">{{text}}</span>
      <img src="./images/pic02.png" alt="" class="box-container__img" />
    </div>
    </a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: "3d-transform效果小demo",
      containerTransform: {
        display: 'block',
        transform: 'rotate3d(0,0,0,0deg)',
        outline: '1px solid transparent'//消除火狐3d效果产生的锯齿
      },
      textTransform: {
        transform: 'transloateX(0px) translateY(0px)'
      }

    }
  },
  mounted: function(){
    let that=this
     document.getElementById("sss").addEventListener("mousemove",that.onTrans3D,false)
     document.getElementById("sss").addEventListener("mouseout",that.onReset,false)
  },
  methods: {
    onTrans3D() {
      let rect = this.$refs.i.getBoundingClientRect() //获取card位置属性
      var xl = this.$refs.i.clientWidth / 2 //获取card宽度
      var yl = this.$refs.i.clientHeight / 2 //获取card高度
      var dtop = rect.top //获取card位置的高度
      var dleft = rect.left //获取card位置的宽度
      var mtop = event.clientY //获取鼠标点的位置
      var mleft = event.clientX
      var xm = mleft - dleft //与card之间的相对位置
      var ym = mtop - dtop;
      //通过相对位置算出旋转方向，与旋转角度
      var px = 0,
        py = 0
      px = (yl - ym) / yl
      py = (xm - xl) / xl
      var pz = 0
      var rotate = "rotate3d(" + px + "," + py + "," + pz + ",15deg)"
      this.containerTransform.transform = rotate
      console.log(rotate)
    },
    onReset() {
      var rotate = "rotate3d(0,0,0,15deg)"
      this.containerTransform.transform = rotate
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.box {
  display: flex;
  width: 100%;
  height: 100%;
  justify-content: space-around;
  align-items: center;
  &-container {
    position: relative;
    border: 0;
    transition: all 0.2s ease;
    &__text {
      position: absolute;
      color: #fff;
      font-size: xx-large;
      font-weight: bold;
      text-shadow: 2px 2px 2px #000;
      bottom: 40px;
      left: 20px;
      transition: all 0.2s ease;
      z-index: 100;
    }
    &__img {
      display: block;
      transform: all 0.2s ease;
    }
  }
}
#sss{
  perspective: 800px;
  perspective-origin: 50% 50%;
  transform-style: preserve-3d;
}
</style>
