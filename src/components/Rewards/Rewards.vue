<template>
  <div class="rewards">
    <div class="rewards_container __container">
      <div>
        <h1>получили <br />20 наград</h1>
        <p>в различных номинациях</p>
      </div>
      <img src="/reward.svg" alt="" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.rewards {
  background-color: #fbd927;
}

.rewards_container {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;

  img {
    width: 60%;
  }

  h1 {
    color: #57a03c;
    text-transform: uppercase;
    font-size: 50px;
    font-weight: 700;
  }

  p {
    margin-top: 10px;
    font-size: 18px;
    font-weight: 600;
  }
}
</style>
