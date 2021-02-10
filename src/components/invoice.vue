<template>
  <div class="hello">
    <header id="head">INVOICE</header>
   <div id="Name"> 
     Enter Your Name:-<input type="text" id="Name" name="Name" placeholder="Enter your Name..." v-model="invoice.Name" >
   </div>
   <div id="address"> 
     Enter Your Address:-<input type="text" id="address" name="address" placeholder="Enter your Address..." v-model="invoice.Address" >
   </div>
   <div id="Gmail"> 
     Enter Your Gmail:-<input type="text" id="Gmail" name="Gmail" placeholder="abc@Gmail.com..." v-model="invoice.Gmail" >
   </div>
   <div id="Date">
     <label for="Date">Date :-</label> <input type="date" id="Date" name="Date" v-model="invoice.Date">
   </div>
   <div id="Material"> 
     Enter your Amount of Material:-<input type="text" id="Material" name="Material" placeholder="Amount of Material.." v-model="invoice.Material"  >
   </div>
   <div id="Labor"> 
     Enter your Total Number of Labor:-<input type="text" id="Labor" name="Labor" placeholder="Number Labor.." v-model="invoice.Labor" @change="Price" >
   </div>
    <div id="Price"> 
     Price:-<input disabled type="text" id="Price" name="Price" placeholder="Price.." v-model="invoice.Price" @change="Tax" >
   </div>
   <div id="Tax"> 
     Tax:-<input disabled type="text" id="Tax" name="Tax" placeholder="Tax.." v-model="invoice.Tax"  >
   </div>
   <div id="Total"> 
     Total:-<input disabled type="text" id="Total" name="Total" placeholder="Total.." v-model="invoice.Total" >
   </div>
   <button> SUBMIT </button>
  </div>
  
  
</template>

<script>
export default {
  data() {
    return {
      invoice: {
        Name: null,
        Gmail: null,
        Date: null,
        Address: null,
        Material: "",
        Labor: "",
        Price:"",
        Tax:"",
        Total:"",
        
      },
  
    }

  },
  methods:{
   
    Price() {
      this.invoice.Price =
        `${
          parseFloat(this.invoice.Labor) *
          parseFloat(this.invoice.Material)
        }` + " /-";
        this.invoice.Tax = `${ 
        parseFloat(this.invoice.Price)*12/100
        }` + "/-";
        this.invoice.Total = `${
          parseFloat(this.invoice.Price) +
          parseFloat(this.invoice.Tax)
        }` + " /-";
    },

  }

}
</script>


<style scoped>
.hello{
  background-color: lightcoral;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
#head {
  height: 45px;
  width: 100%;
  background-color: gray;
  color: aliceblue;
  letter-spacing: 20px; 
}
#head:hover{
  background-color: brown;
  color: blue;
}

#Name{

    padding: 3px;
    margin: 5px;
    

}
#address{

    padding: 20px;
    margin: 5px;
    

}
#Gmail{

    padding: 3px;
    margin: 5px;    
}
#Date{
    
    padding: 3px;
    margin: 5px;

}
#Material{
    
    padding: 3px;
    margin: 5px;

}
#Labor{
    
    padding: 3px;
    margin: 5px;

}
#Price{
    
    padding: 3px;
    margin: 5px;

}
#Tax{
    
    padding: 3px;
    margin: 5px;

}
#Total{
    
    padding: 3px;
    margin: 5px;

}
</style>
