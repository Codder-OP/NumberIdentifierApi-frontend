<template>
  <div>
    <form>
      <div class="form-row">
        <div class="col-4"><b> User Input: </b>
          <input id="inputNumber" v-model="inputNum" type="number" placeholder="Enter a Number" />
          <button id="button" type="button" style="cursor:pointer;font-size:12px !important;background-color: #238C4;border:solid 1px #0D75A8; height:20px;margin-left:10px" @click="submit()">Submit</button>
        </div>
      </div>
    <h1 style="color:green">{{ msg }}</h1>
    </form>
    
     
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  props: {
    //msg: String
  },
  data() {
    return {
      inputNum:'',
      msg:''
    }
  },
  methods: {
    submit(){
      axios.get('http://localhost:8000/api/checknumber',{
      params: {
        number:this.inputNum
      }
      }).then(response => {
        console.log(response.data);
        this.msg = response.data
      })
      .catch(error => {
        console.log(error)
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
