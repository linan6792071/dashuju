<template>
    <div class="datacontent">
       <dataconcen></dataconcen>
      <data-con-right  :DataRight='DataRight'></data-con-right>
    </div>
</template>

<script>
    import DataConLeft from "./DataConLeft";
    import DataConCen from "./DataConCen";
    import DataConRight from "./DataConRight";
    export default {
        name: "DataContent",
      components: {DataConRight, DataConCen, DataConLeft},
      props:["DataRight"],
    }
</script>

<style scoped>

</style>
