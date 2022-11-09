<template>
  <div class="hello">
    <h1>{{ gemiddeldCaramelGebruik }}</h1>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import axios from "axios";
export default class HelloWorld extends Vue {
  private gemiddeldCaramelGebruik = "Nog niet opgehaald";

  created(){
    console.log("testlijntje");
    this.GetStats("");
  }

  private GetStats(params:any) {
    console.log("test");
    axios.get("https://localhost:7074/api/v1/Statistic/flavor/6368fb431e737543aa41a34a/2").then((data) => {
      this.gemiddeldCaramelGebruik = String(data.data[0].type) +  "   " +  String(data.data[0].total);
      console.log(data);
      }).catch((error)=>{console.log(error);});
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
