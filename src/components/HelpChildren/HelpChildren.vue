<template>
  <div class="help_children">
    <div class="help_children_container __container">
      <img src="/heart.svg" alt="" />
      <div>
        <h1>на помощь <br />деткам</h1>
        <p>пожертвования детским домам</p>
      </div>
    </div>
  </div>
</template>
<style lang="scss" scoped>
.help_children {
  background-color: #fffbde;
}
.help_children_container {
  display: flex;
  align-items: center;
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
