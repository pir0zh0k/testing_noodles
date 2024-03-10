<script></script>

<template>
  <div class="warm_moments">
    <div class="warm_moments_container __container">
      <h1>Теплые моменты <br />с роллтон</h1>
      <h2>Продали <br />2 млн км <br />лапши</h2>
      <p>что равно 50-ти обхватам <br />Земли</p>
      <img class="planet" src="/planet.svg" alt="" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.warm_moments {
  width: 100vw;
  height: 100vh;
  background-color: #fbd927;
}

.warm_moments_container {
  padding-top: 80px;
  position: relative;

  h1 {
    color: #df231d;
    text-transform: uppercase;
    font-size: 40px;
    font-weight: 700;
  }

  h2 {
    font-size: 55px;
    margin-top: 100px;
    text-transform: uppercase;
    color: #57a03c;
    font-weight: 600;
  }

  p {
    margin-top: 10px;
    font-size: 18px;
    font-weight: 600;
  }

  .planet {
    position: absolute;
    width: 70%;
    right: 0;
    top: 0;
  }
}
</style>
