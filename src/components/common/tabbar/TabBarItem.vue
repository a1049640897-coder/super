
<template>
  <div id="tab-bar-item" @click="itemClick" >
    <div v-if="!isActive"><slot name="icon"></slot></div>
    <div v-else><slot name="active-icon" ></slot></div>
    <div :class="{active:isActive}"><slot name="text"></slot></div>
  </div>
</template>

<script>
	export default {
    name: "TabBarItem",
    props:{
      path:String,
    },
    data(){
      return{

      }
    },
    methods:{
      itemClick(){
        this.$router.push(this.path);
      }
    },
    computed:{
      isActive(){
      return   this.$route.path.indexOf(this.path)!==-1;
      }
    }
  }
</script>

<style scoped>
  #tab-bar-item {
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
  }
  #tab-bar-item img{
    width: 24px;
    height: 24px;
    margin-top: 3px;
  }
  .active {
    color: red;
  }

</style>