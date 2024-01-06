

<template>
  <header class="header">
    <FormComp  >
        <div class="yeeti-box">
           
          <img v-if="clicked && show" src="./assets/avatar3 (2).jpg" alt="test image" class="img" />
          <img v-else-if="!clicked && !show" src="./assets/avatar1.png" alt="test image" class="img" />
          <img v-else src="./assets/avatar2.png" alt="test image" class="img" />
          
        </div>
        
        <input class="form__input form_bod" type="text" id="name" placeholder="Name" v-model="name"/>
        
        <input class="form__input form_bod" type="text" id="password" placeholder="Enter password" v-model="password" v-if="selected" @keyup="onClick" />

        <input class="form__input form_bod" type="password" id="password" placeholder="Enter password" v-model="password" v-else @keydown="onClick" @keyup="onRelease"/>
        
        <div class="form__pass">

          <input type="checkbox" id="checkbox" v-model="selected"/>
          <label  class="form__name" for="checkbox" >Show password {{ Pass }}</label>
        </div>
        <button  class="form__btn" type="submit" @click.prevent="onSubmit">submit</button>
    </FormComp>
  </header>

   
</template>



<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>


<script >
 import FormComp from "./components/Form.vue"
 
   export default {
     name:"App",
     components:{
     FormComp},
     
     data(){
       return{
         name:"",
         password:"",
         Pass:"",
         inputType:"password",
         selected:false,
         alt:"3d model",
         clicked:false,
         show:false
 
      }
    },
    methods:{
      onSubmit(){
        alert("submitted!" )
      },
      showPass(){
         if(this.showPass){
                 
                this.inputType = "text"
         }
      },
      onClick(){
        this.clicked = true,
        this.show = true
         
         
      },
      onRelease(){
          const prog = ()=> this.clicked = false

        setTimeout((prog),2000)
      }      

    }
    
  }
    
  </script>