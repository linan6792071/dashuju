<template>
 <div class="data_con_left">
   <div class="left_top">
     <div class="left_top_info">
       <div class="info_title">实时统计</div>
       <span class="borders1"></span>
       <span class="borders2"></span>
       <span class="borders3"></span>
       <span class="borders4"></span>
       <div class="infos_main">
         <div class="infos_1">
           <div><img src=""></div>
           <div>
             <p>车辆总数(辆)</p>
             <p>12457</p>
           </div>
         </div>
         <div class="infos_2"></div>
         <div class="infos_3"></div>
         <div class="infos_4"></div>
       </div>
     </div>
     <div class="left_top_jobs">

     </div>
   </div>
   <div class="left_btn"></div>
 </div>
</template>

<script>
    export default {
        name: "DataConLeft"
    }
</script>

<style scoped>
  .data_con_left{width: 25%;height: 100%;}
.left_top{width: 100%;height: calc(75% - 20px);margin-bottom: 20px;position: relative;}
 .left_top_info{
   height: 62%;width: 100%;
   border: 1px solid #20558b;
   box-sizing: border-box;
   position: relative;
 }
 .info_title{
   width: 158px;height: 43px;
   background: url(../../static/img/info-title.png) no-repeat;
   position: absolute;top: -22px;left: 50%;margin-left: -74px;color: #fff;
   font-size: 18px;font-weight: 600;line-height: 43px;text-align: center;
 }
 .left_top_jobs{
    height: calc(38% - 20px);
    width: 100%;
    background-color: rgba(0,24,106,0.5);
    margin-top: 20px;
    border: 1px solid #20558b;
    box-sizing: border-box;
    position: relative;
  }
 .left_btn{
    width: 100%;
    height: 25%;
    background-color: rgba(0,24,106,0.5);
    border: 1px solid #20558b;
    box-sizing: border-box;
    position: relative;
  }
  .infos_main{width: 100%;height: 80%;}
  .infos_1{
    width: 100%;
    height: 25%;
    margin: 8px auto;
    background: url("../../static/img/info-text.png") no-repeat;
  }
</style>
