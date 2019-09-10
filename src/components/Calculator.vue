<template>
<div>
<div class="cal">
<div class="display" v-if="num">{{num || "0"}}</div>
<div class="display" v-else>0</div>
<div class="btn blueborder" @click="clear">C</div>
<div class="btn blueborder" @click="sign">+/-</div>
<div class="btn blueborder"  @click="percent">%</div>
<div class="operator btn" @click="divide">/</div>
<div class=" btn" @click="add('7')">7</div>
<div class="btn" @click="add('8')">8</div>
<div class="btn" @click="add('9')">9</div>
<div class="operator btn" @click="times">x</div>
<div class="btn" @click="add('4')">4</div>
<div class="btn"@click="add('5')">5</div>
<div class="btn" @click="add('6')">6</div>
<div class=" operator btn" @click="minus">-</div>
<div class="btn" @click="add('1')">1</div>
<div class="btn" @click="add('2')">2</div>
<div class="btn" @click="add('3')">3</div>
<div class="operator btn" @click="plus">+</div>
<div class="zero" @click="add('0')">0</div>
<div class="btn blueborder" @click="dot">.</div>
<div class="operator btn green" @click="equal">=</div>
</div>
</div>

</template>

<script>
export default {
  data (){
    return {
    num:"",
    operator:null,
    saved:null,
    operation:false
    }
  }
  ,methods:{
    clear(){
      this.num =""
    },
    sign(){
      this.num = this.num.charAt(0) === "-" ? this.num.slice(1) :`-${this.num}`
    },
    percent(){
      this.num=`${parseFloat(this.num)/100}`
    },
    add(num){
      if(this.operation){
        this.num="";
        this.operation=false
      }
this.num=`${this.num}${num}`
    },
    dot(){
      if(this.num.indexOf('.') === -1){
        this.add('.')
      }
    },
      divide(){
        this.operator=(a,b)=>a/b
        this.operation=true;
        this.saved=this.num

      }, plus(){
         this.operator=(a,b)=>a+b 
          this.operation=true
                this.saved=this.num
      },
       minus(){
         this.operator=(a,b)=>a-b 
          this.operation=true
                this.saved=this.num
      },
       times(){
         this.operator=(a,b)=>a*b 
          this.operation=true
                this.saved=this.num
      },
    equal(){
      this.num=`${this.operator(
         parseFloat(this.num),
         parseFloat(this.saved))}`
         this.saved=null
  
    }
  }

  }

</script>

<style scoped>

.cal{
width: 321px;
  margin:0 auto;
  display:grid;
  grid-template-columns:repeat(4,1fr);
  grid-auto-row:minmax(50px,auto);
  background-color:#1B1845;
      padding: 25px;
       border-radius:17px;

}
.display{
  justify-content: center;
    grid-column: 1/5;
    background-color: #221E52;
    color: white;
    height: 70px;
    display: flex;
    align-items: center;
    border-radius:17px;
        margin-bottom: 20px;

}
.zero{

  grid-column: 1/3;
    height: 70px;
    background-color: #453F8C;
    margin:5px;
    color:white;
     display: flex;
     border-radius:17px;
    vertical-align: middle;
    text-align: center;
    align-items: center;
    justify-content: center;
    cursor:pointer
}
.btn{
  background-color:#5A54B3;
  cursor:pointer;
  color:white;
  width: 70px;
    height: 70px;
  border-radius: 17px;
    display: flex;
    vertical-align: middle;
margin:5px;
    align-items: center;
    justify-content: center;
}
.operator{
  background-color:#ED5E13;
  color:white;
   cursor:pointer
}
.blueborder{
  background-color:#1B1845;
  border:1px solid #2C2667
}
.green{
  background-color:#79C429
}
</style>
