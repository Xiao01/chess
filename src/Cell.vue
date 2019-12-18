<template>
  <div id="app" class="cell" v-on:click="onClickSelf">
    <template v-if="a">{{x}}</template>
    <template v-else></template>
  </div>
</template>
<style >
.cell {
  border: 1px solid black;
  width: 100px;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 80px;
}
</style>
<script>
export default {
  props: ["n","isfinshed"],
  data() {
    return {
      a: false,
      x: null,
    };
  },
  methods: {
    onClickSelf() {
      console.log( this.n)
      console.log( this.isfinshed)
      if(this.isfinshed){return}
      if(this.a){return}
       this.x= this.n %2 ==0? "X" :"O";
      (this.a = true), this.$emit("click",this.x);
    }
  }
};
</script>