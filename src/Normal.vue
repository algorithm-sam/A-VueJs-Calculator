<template>
  <div id="button_container" @click="buttonClick">
        <div class="basic_cntrl">
              <p class="cntrl"> 9</p>
              <p class="cntrl"> 8</p>
              <p class="cntrl"> 7</p>

              <p class="cntrl"> &radic;</p>
              <p class="cntrl"> 6</p>
              <p class="cntrl"> 5</p>
              <p class="cntrl"> 4</p>
              <p class="cntrl"> x²</p>
              <p class="cntrl"> 3</p>
              <p class="cntrl"> 2</p>
              <p class="cntrl"> 1</p>
              <p class="cntrl"> (</p>
              <p class="cntrl"> .</p>
              <p class="cntrl "> 0</p>
              <p class="cntrl"> -</p>
              <p class="cntrl"> )</p>

  </div>

      <div class="cntrls">
        <p class="cntrl adcntrl">&larr;</p>
        <p class="cntrl adcntrl">CE</p>
        <p class="cntrl adcntrl">/</p>
        <p class="cntrl adcntrl">*</p>
        <p class="cntrl adcntrl">+</p>
        <p class="cntrl adcntrl">=</p>
      </div>
  </div>
</template>

<script>
export default {
  name:'basic',

    data(){
      return{

      }
    },

    methods:{
        buttonClick:function(evt){
          this.$emit('buttonClicked',evt.target);
        }
    }

}
</script>

<style scoped>
  #button_container{
  padding:5px 2px;
  margin-top:30px;
  box-sizing: border-box;
}

#button_container::before,#button_container::after{
  content:' ';
  display: table;
}

#button_container::after{
  clear: both;
}
.cntrl{
  width:24%;
  height:50px;
  box-sizing: border-box;
  background: #008080;
  border-radius:3px;
  padding: 10px;
  border:none;
  color:white;
  display: inline-block;
  margin-bottom: 5%;
  cursor: pointer;
}

.cntrl:hover{
  background: rgb(0,0,100);
}

.cntrls{
  width:28%;
  float:right;
}
.adcntrl{
  height:80px;
  width:48%;
  padding:25px;
  background: #196;
}

.basic_cntrl{
  width:70%;
  float:left;
}

</style>
