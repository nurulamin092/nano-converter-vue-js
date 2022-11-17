<template>
  <div id="app">
    <div class="container">
        <!-- header section -->
       <header id="title">
            <h1>Nano Converter System</h1>
       </header>

       <!-- Main content section -->
     <!-- <main>
        <section>
            <h2>Number  System Conversion</h2>
            <div class="box">
                <div class="input-group"> 
                    <label for="">Decimal</label>
                    <input type="text"
                     placeholder="Input Any Decimal Number, eg. 332323"
                     name="" id="">
                </div>
                
                   <div class="input-group"> 
                    <label for="">Binary</label>
                    <input type="text" 
                    placeholder="Input Any Decimal Binary, eg. 111001010"
                    
                    name="" id="">
                </div>
              
                   <div class="input-group"> 
                    <label for="">Octal</label>
                    <input type="text" name="" id=""
                    placeholder="Input Any Octal Number, eg. 452144"
                    >
                </div>
              
                   <div class="input-group"> 
                    <label for="">Hexadecimal</label>
                    <input type="text" name="" id=""
                    placeholder="Input Any Hexadecimal Number, eg. AF14451"
                    >
                </div>
               <div class="reset-btn-container">
                 <button>Reset</button> 
               </div> 
               <div class="one-rem-space"></div>
            </div>
               
         </section>
         <section>
             <h2>Text Conversion</h2>
             <div class="box">
                <div class="input-group">
                    <label for="">Enter Your Text Below</label>
                    <textarea name="text-filed" id="" cols="30" rows="10"></textarea>
                </div>
                <div class="half-rem-space"></div>
                <div  class="input-group">
                    <label for="">Enter Your Binary Below</label>
                    <textarea name="binary-filed" id="" cols="30" rows="10"></textarea>
                </div>
                <div class="reset-btn-container">
                    <button>Reset</button> 
                  </div> 
                  <div class="one-rem-space"></div>
             </div>
         </section>
     </main> -->
     <section>
            <h2>Number  System Conversion</h2>
            <div class="box">
                <div class="input-group"> 
                    <label for="">Decimal</label>
                    <input type="text"
                     placeholder="Input Any Decimal Number, eg. 332323"
                     v-model="numbers.decimal"
                     name="" id="">
                </div>
                
                   <div class="input-group"> 
                    <label for="">Binary</label>
                    <input type="text" 
                    placeholder="Input Any Decimal Binary, eg. 111001010"
                    v-model="numbers.binary"
                    name="" id="">
                </div>
              
                   <div class="input-group"> 
                    <label for="">Octal</label>
                    <input type="text" name="" id=""
                    placeholder="Input Any Octal Number, eg. 452144"
                   v-model="numbers.octal"
                    >
                </div>
              
                   <div class="input-group"> 
                    <label for="">Hexadecimal</label>
                    <input type="text" name="" id=""
                    placeholder="Input Any Hexadecimal Number, eg. AF14451"
                    v-model="numbers.hexadecimal"
                    >
                </div>
               <div class="reset-btn-container">
                 <button>Reset</button> 
               </div> 
               <div class="one-rem-space"></div>
            </div>
               
         </section>
         <section>
             <h2>Text Conversion</h2>
             <div class="box">
                <div class="input-group">
                    <label for="">Enter Your Text Below</label>
                    <textarea name="text-filed" id="" cols="30" rows="10"></textarea>
                </div>
                <div class="half-rem-space"></div>
                <div  class="input-group">
                    <label for="">Enter Your Binary Below</label>
                    <textarea name="binary-filed" id="" cols="30" rows="10"></textarea>
                </div>
                <div class="reset-btn-container">
                    <button>Reset</button> 
                  </div> 
                  <div class="one-rem-space"></div>
             </div>
         </section>
    </div>
  </div>
</template>

<script>
require('@/assets/style/reset.css');
require('@/assets/style/fonts.css');
require('@/assets/style/style.css');

function isBinary(text){
  for (const t of text) {
    if (t!== '0' && t !== '1') return false   
  }
  return true
}

function isOctal (text) {
  for (const t of text) {
    if (t< '0' || t> '7') return false
  }
  return true
}


export default {
  name: "App",
  data(){
    return{
      numbers:{
        decimal:0,
        binary:0,
        octal:0,
        hexadecimal:0
      },
      invalidNumber : false
    }
  },
  watch:{
    'numbers.decimal': function(value){
      this.numbers.decimal = parseInt(value) ||0;
      this.numbers.binary = value.toString(2);
      this.numbers.octal = value.toString(8);
      this.numbers.hexadecimal = value.toString(16);
    },
    'numbers.binary': function (value){
      let decimal = parseInt(value,2)
      if (!isBinary(value)) {
        this.invalidNumber = true
      } else{
        this.invalidNumber = false
      }
      this.numbers.decimal = decimal,
      this.numbers.binary = value || 0,
      this.numbers.octal = decimal.toString(8),
      this.numbers.hexadecimal = decimal.toString(16)

    },
    'numbers.octal': function(value){
      let decimal = parseInt(`0${value}`,8) || 0
      if(!isOctal(value)){
        this.invalidNumber = true
      }
      else{
        this.invalidNumber = false
      }
      this.numbers.decimal = decimal,
      this.numbers.binary = decimal.toString(2) || 0,
      this.numbers.octal = value || 0,
      this.numbers.hexadecimal = decimal.toString(16)
    }
  }
};
</script>
