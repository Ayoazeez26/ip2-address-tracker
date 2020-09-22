<template>
  <div class="ip-display flex font-bold flex-col md:flex-row justify-around items-center text-center md:text-left bg-white shadow-2xl w-11/12 md:w-10/12 z-50">
    <div class="address mt-4 mb-4 md:self-start md:mt-8 md:mb-8">
      <h5 class="text-xs md:text-base md:tracking-widest md:mb-3">IP ADDRESS</h5>
      <p class="text-black text-xl md:text-3xl">{{ip}}</p>
    </div>
    <div class="line w-px h-20 hidden md:block bg-gray-600"></div>
    <div class="location mb-4 md:mt-8 md:mb-8">
      <h5 class="text-xs md:text-base md:tracking-widest md:mb-3">LOCATION</h5>
      <p class="text-xl md:text-3xl">{{city}}, {{region}}<br class="hidden md:block">{{postal}}</p>
    </div>
    <div class="line w-px h-20 hidden md:block bg-gray-600"></div>
    <div class="timezone mb-4 md:mt-8 md:self-start md:mb-8">
      <h5 class="text-xs md:text-base md:tracking-widest md:mb-3">TIMEZONE</h5>
      <p class="text-xl md:text-3xl">UTC {{timezone}}</p>
    </div>
    <div class="line w-px h-20 hidden md:block bg-gray-600"></div>
    <div class="isp mb-4 md:self-start md:mt-8 md:mb-8">
      <h5 class="text-xs md:text-base md:tracking-widest md:mb-3">ISP</h5>
      <p class="text-xl md:text-3xl">{{isp}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['ip', 'city', 'region', 'postal', 'timezone', 'isp']
}
</script>

<style scoped>
.ip-display {
  border-radius: 1.2rem;
  position: absolute;
  bottom: -100px;
}
.ip-display h5 {
  color: hsl(0, 0%, 59%);
}
@media screen and (max-width: 768px) {
  .ip-display {
    border-radius: 0.6rem;
  bottom: -150px;
  }
}
</style>