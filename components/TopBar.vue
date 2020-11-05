<template>
  <div>
    <div class="top-element">
      <form method="get">
        <input
          id="search"
          type="text"
          placeholder="search"
          name="search"
          class="search"
        >
      </form>
      <div class="profile">
        <img src="../static/images/user.jpg">
        <p>John Doe</p>
      </div>
    </div>
    <div class="bottom-element">
      <div class="breadcrum">
        <p>Home > LA</p>
      </div>
    </div>
  </div>
</template>
<style lang="scss" scoped>
.top-element{
  position: absolute;
  top: 0;
  height: 80px;
  z-index: 0;
  width: calc(100% - 60px);
  margin-left: 60px;
  border-bottom: 1px solid #e9ecef;
  padding: 1rem 1rem;
  display: flex;
  flex-flow: row nowrap;
  justify-content: flex-start;
  align-items: center;
  background-color: $primary;
  color: white;
  form{
    flex-flow: row wrap;
    align-items: center;
    input{
      width: 350px;
      transition: all 0.15s cubic-bezier(0.68, -0.55, 0.265, 1.55);
      border-color: rgba(0, 0, 0, 0.6);
      background-color: rgba(255, 255, 255, 0.9);
      border-radius: 2rem;
      padding: 0.5rem 0.5rem;
      font-weight: 400;
      align-items: center;
    }
  }
  .profile{
    display: flex;
    flex-direction: row;
    margin-left: auto;
    align-items: center;
    img{
      font-size: .875rem;
      width: 36px;
      height: 36px;
      border-radius: 50%;
    }
    p{
      align-items: center;
      margin:0 0 0 0.5rem;
    }
  }
}
.bottom-element{
  position: absolute;
  top: 80px;
  height: 120px;
  z-index: 0;
  width: calc(100% - 60px);
  margin-left: 60px;
  display: flex;
  flex-flow: row nowrap;
  justify-content: flex-start;
  align-items: center;
  background-color: $primary;
  color: white;
}
</style>
<script>
export default {
  data () {
    return {
      isActive: false,
      test: true
    }
  },
  methods: {
    myFilter () {
      this.isActive = !this.isActive
    }
  }
}
</script>
