<template>
  <div id="app">
      <div id="calculator">
        <p class="title">{{ mode }} Mode</p>
          <p id="resultScreen">
            <!-- <input type="text" id="input" ref="input" disabled :value="current"/> -->
            <textarea  id="input" :value="current" disabled></textarea>
          </p>
          <br />

          <p class="toggle" @click="toggleMode"> &harr; Toggle Basic/Advanced View </p>

          <Normal v-if="isBasic" @buttonClicked="buttonClicked"/>
          <Scientific v-else @buttonClicked="buttonClicked"/>
      </div>
  </div>
</template>

<script>

String.prototype.InsertBegin=function(CharToInsert){
     return CharToInsert + this;
}

import Normal from './Normal';
import Scientific from './Scientific';
export default {
  name: 'Calculator',
  data () {
    return {
      msg: 'a simple calculator using vueJs',
      mode:'Basic',
      isBasic:true,
      current:0,
    }
  },
  components:{
    Normal,
    Scientific
  },
  methods:{
    toggleMode:function(){
      if(this.isBasic === true){
        this.mode='Advanced';
      }else{
        this.mode='Basic';
      }
      this.isBasic = !this.isBasic;
    },
    compute:function(){
        var vallue=eval(this.current);
        this.current=vallue;

    },

    buttonClicked:function(target){
      // this.current+=e;

      if(target.tagName !='P'){
        return false;
      }
      var text=target.innerText;
      if(this.current==0){
        this.current='';
      }
      switch(text){
        case 'CE' :
          this.current=0;
          this.arithmetic_equiv=0;
          break;
        case 'Sin':
          // this.current+=this.unary('sin',val);
          this.current= Math.sin(this.current);
          break;
        case 'Cos':
          this.current= Math.cos(this.current);
          // this.current+='(cos(';
          break;
        case 'Tan':
          // this.current+=this.unary('tan',val);
          // this.current+='(tan(';
          this.current= Math.tan(this.current);
          break;
        case 'Log':
          // this.current+=this.unary('log',val);
          // this.current+='(log(';
          this.current= Math.log(this.current);
          break;

        case '=' :
          this.compute();
          break;
        case '√' :
          this.current=Math.sqrt(this.current);
          break;
        case 'π' :
          this.current=Math.PI;
          break;
        case '%' :
          this.current=this.current/100;
          break;
        case 'x²' :

          this.current=Math.pow(this.current,2);
          break;

        case '±' :
              if(this.current[0] !='-' && this.current[0] !='0'){

                  this.current= '-'+ this.current;

              }else if(this.current[0]=='-'){

                this.current=this.current.slice(1);

              }
          break;

        case '←':
            this.current= this.current.substring(0,this.current.length-1);
            break;

        case 'Deg':
            this.current= this.current * (180/Math.PI);
            break;

        default :this.current+=text;
                this.arithmetic_equiv+=text;
                break;
      }
    }
  }

}
</script>

<style scoped>
#app{
  padding-top:  50px;
}
    p.title{
      color:white;
      font-size:1.5em;
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
      text-transform: capitalize;
      text-align: center;
      margin-bottom:20px;
    }

#calculator{
  margin-top:50px;
  text-align: center;
  border: 1px solid #ccc;
  width:35%;
  margin: 0 auto;
  padding:20px;
  border-radius: .5rem;
}
#input{
  text-align:right;
  width:95%;
  font-size:2em;
  padding:10px;
  padding-right: 30px;
  height:50px;
  border-radius: 5px;
  border:none;
  font-weight: bold;
  resize: none;
  color: rgb(0,100,0);
}
.toggle{
  color:white;
  padding:10px;
  margin-top:20px;
  font-size:1.2em;
  cursor:pointer;
  width:50%;
  margin:0 auto;
  background:#58a;
}
.toggle span input{
  padding:10px;
}
.toggle span{
  margin-right:5%;
}

.adcntrl{
  height:70px !important;
}

</style>
