<template >
  <div  >
    <div class="jing">井字棋</div>
    <div>{{desc}}</div>
    <div class="row" >
      <Cell @click="onClickCell(0,$event)" :n="n" :isfinshed="isfinshed"/>
      <Cell @click="onClickCell(1,$event)" :n="n" :isfinshed="isfinshed" />
      <Cell @click="onClickCell(2,$event)" :n="n" :isfinshed="isfinshed" />
    </div>
    <div class="row" >
      <Cell @click="onClickCell(3,$event)" :n="n" :isfinshed="isfinshed" />
      <Cell @click="onClickCell(4,$event)" :n="n" :isfinshed="isfinshed" />
      <Cell @click="onClickCell(5,$event)" :n="n" :isfinshed="isfinshed" />
    </div>
    <div class="row" >
      <Cell @click="onClickCell(6,$event)" :n="n" :isfinshed="isfinshed" />
      <Cell @click="onClickCell(7,$event)" :n="n" :isfinshed="isfinshed" />
      <Cell @click="onClickCell(8,$event)" :n="n" :isfinshed="isfinshed" />
    </div>
  </div>
</template>

<script>
import Cell from "./Cell.vue";

export default {
  components: {
    Cell
  },
  methods:{
    onClickCell(i,event){
      this.map[Math.floor(i/3)][i%3]=event
      console.log( Math.floor(i/3) +","+i%3+ "被点击了，内容是" + event );
      this.n = this.n+1;
      const map = this.map;
      for(let i=0;i<2;i++){
          if(
            map[i][0] != null && 
            map[i][0] == map[i][1]&& 
            map[i][1] == map[i][2]){
              this.isfinshed =true
              this.result=",赢家是: " + map[i][0]
          }else if(
            map[0][i] != null && 
            map[0][i] == map[1][i]&& 
            map[1][i] == map[2][i]){
              this.isfinshed =true
              this.result=",赢家是: " +map[0][i]
          }
      }
      if( map[0][0]!= null &&  map[0][0]==map[1][1] && map[1][1]==map[2][2]){
          this.isfinshed =true
          this.result=",赢家是: " +map[0][0]
      }else if(map[0][2]!= null &&  map[0][2]==map[1][1] && map[2][0]==map[1][1]){
          this.isfinshed =true
          this.result=",赢家是: " +map[0][2]
      }
     
      this.desc="第"+this.n+"手"
      if(this.isfinshed ==true){
        this.desc="游戏结束,"+ this.desc + this.result
      }
    }
  },
  data(){
    return { 
      n : 0,
      map:[[null,null,null],[null,null,null],[null,null,null]],
      result:"",
      isfinshed:false,
      desc:"开始游戏"
      }
  }
};
</script>

<style>

.row {
  display: flex;
}
.jing {
  width: 300px;
  background:darkgrey;
  text-align:center;
  font-size: 30px;
}
</style>
