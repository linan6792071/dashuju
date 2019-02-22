<template>
    <div id="carintent">
   <data-title></data-title>
       <data-content :DataRight='DataRight'></data-content>
    </div>
</template>

<script>
   import "../../static/css/index.css"
   import DataTitle from "../components/DataTitle";
   import DataRight from "../data/DataRight"
   import DataContent from "../components/DataContent";
    export default {
        name: "CarIntenet",
      components: {DataContent, DataTitle},
      data(){
        return {
            DataRight
        }
      }
    }
</script>

<style scoped>
#carintent{
  width: 100%;
  height: 100%;
  background: url("../../static/img/map_bg.png");
  background-size: cover;
}
</style>
