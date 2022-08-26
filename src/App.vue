<script >
var alphabet = ["A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z"];
import Grid from './components/Grid.vue';
export default
  {
    components:{
      Grid
    },
    data() {
        return {
            message: "ok",
            isHidden: true,
            rows: 2,
            columns: 2,
            rc: 2,
            gridCount: 2,
        };
    },

    methods: {
       myFilter: function() {
      this.isActive = !this.isActive;
      // some code to filter users
    },
        genGrid() {
            console.log("click me ");
            this.rows = +this.rc;
            this.columns = +this.rc;
        },
        iniAlphabet() {
            alphabet = ["A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z"];
        },
        
        randomNumber : function(){
      //     return Math.floor(Math.random() * (10 - 1 + 1)) + 1;
      //     var result           = '';
      //     var characters       = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
      //     var charactersLength = characters.length;
      //     for ( var i = 0; i < length; i++ ) {
      //       result += characters.charAt(Math.floor(Math.random() * 
      // charactersLength));
      //   }
      //   return result;

      
      const random = Math.floor(Math.random() * alphabet.length);
      const el = alphabet.splice(random, 1)[0];
      const index = alphabet.indexOf(el);
      if (index > -1) { // only splice array when item is found
        alphabet.splice(index, 1); // 2nd parameter means remove one item only
      }
      return el;
      // console.log(el);
        }
      

    },
    components: { Grid }
}


</script>

<template>
<div id="app" class="flex flex-col justify-center items-center">
  <div class="w-700px h-62px p-7px bg-white br-4px filters">
    <div class="flex flex-row items-center">
		<div class="form-element">
			<label class="text" for="select-rows">Number of Grids</label>
			<select v-on:change="isHidden = true" id="select-rows" v-model="rows">
				<option v-for="i in 5" :value="i">{{ i }}</option>
			</select>
		</div>
		<div class="form-element">
           <!-- Generate <input type="number" :value="rows" /> random grid, with
      <input type="number" v-model="columns" />
      rows/columns <button @click="genGrid">Generate</button> -->
      
			<label class="text" for="select-columns">Nomber of rows/columns per Grid</label>
			<select v-on:change="isHidden = true" id="select-columns" v-model="columns">
				<option v-for="i in 5" :value="i">{{ i }}</option>
			</select>
		</div>
    
    <button v-on:click="isHidden = !isHidden" id="gen-grid" class="px-4 py-2 text-white bg-blue-400 border border-blue-200 rounded hover:bg-blue-500 ml-50px">Generate</button>
    
    </div>
	</div>
  <div  v-if="!isHidden" class="flex flex-wrap flex-row justify-evenly w-100% genrate-btn">
  <template v-for="row in rows">
    	<div id="grid" class="grid grid-gap-2 bg-black ml-20px mt-40px outline-solid outline-12" v-bind:style="{ 'grid-template-rows': 'repeat(' + columns + ', 1fr)', 'grid-template-columns': 'repeat(' + columns + ', 1fr)' }">
    
      <template v-for="column in columns">
      
      <!-- {{ row }} -->
        <div id="box" class="flex justify-center items-center w-60px h-60px bg-white font-not-italic font-900" v-for="column in columns">
        <!-- {{ column }} -->
        {{randomNumber()}}
        </div>
      </template>
    </div>
     {{iniAlphabet()}}
  
  </template>
</div>
</div>
</template>

<style>
</style>
