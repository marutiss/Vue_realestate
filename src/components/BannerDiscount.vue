<template>
  <div class="Discount">
  <h4>현금 결제 {{rate}}% 할인중!</h4>
</div>
</template>

<script>
export default {
    name: 'BannerDiscount',
    data(){
      return{
        rate: 30,
      }
    },
  mounted(){
    setInterval(() => {
      if (this.rate==0) {
        clearInterval();
        
      } else {
        this.rate--;
      }
    }, 1000); 
  }, 




}
</script>

<style>
.Discount{
  background-color: aliceblue;
  padding: 10px;
  margin: 10px;
}
</style>