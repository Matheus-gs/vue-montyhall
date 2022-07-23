<template>
  <div class='gift'>
    <div class="gift-tie-1"></div>
    <div class="gift-tie-2"></div>
    <div class="gift-box-cover"></div>
    <div class="gift-box"></div>
  </div>
</template>

<script>
export default {

};
</script>

<style>
.gift {
  width: 100px;
  height: 100px;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  z-index: 10;
}

.gift-tie-1,
.gift-tie-2 {
  background: #b12010;
  position: absolute;
}

.gift-tie-1 {
  width: 15px;
  height: 100%;
}

.gift-tie-2 {
  width: 90%;
  height: 15px;
  top: 50%;
}

.gift-box-cover {
  width: 100%;
  height: 25px;
  background: rgb(4, 119, 67);
}

.gift-box {
  width: 90%;
  height: 100%;
  background: rgb(7, 145, 83);
}
</style>