<style scoped>
#main {
  width: 100%;
  height: 100vh;
}

/* You can keep the global styles here if needed */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.red {
  width: 100px;
  height: 100px;
  background-color: red;
}

.green {
  width: 100px;
  height: 100px;
  background-color: green;
}

.yellow {
  width: 100px;
  height: 100px;
  background-color: yellow;
}

.parent {
  width: 100%;
  height: 100%;
  background-color: lightblue;
  display: flex;
  align-items: center;
  justify-content: space-evenly;

  flex-direction: column;
}

.child1 {
  height: 500px;
  width: 500px;
  border: 2px solid darkblue;
  background-color: red;
}
.child2 {
  height: 500px;
  width: 500px;
  border: 2px solid darkblue;
  background-color: red;
}
.child3 {
  height: 500px;
  width: 500px;
  border: 2px solid darkblue;
  background-color: red;
}

nav {
  width: 100%;
  height: 100px;
  /*  background-color: aqua; */
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 3vw;
  border-bottom: 1px solid #dadada;
}

.nav-items {
  display: flex;
  gap: 4vw;
}

.nav-items i {
  font-size: 2vw;
  display: none;
}

.content {
  width: 100%;
  height: calc(100% - 100px);

  display: flex;
}

.left {
  height: 100%;
  width: 55%;

  padding-top: 2vw;
  padding-bottom: 2vw;
  padding-right: 4vw;
  padding-left: 4vw;
}

.left h1 span {
  color: rgb(109, 184, 216);
}

.heading {
  margin-top: 3vw;
}

.para {
  margin-top: 2vw;
  margin-bottom: 2vw;
}

.button {
  background-color: rgb(109, 184, 216);
  color: black;
  font-size: 1.5vw;
  padding-top: 1rem;
  padding-bottom: 1rem;
  padding-right: 2.5rem;
  padding-left: 2.5rem;
  border-radius: 10px;
  border: 1px solid black;
}

.cont-btn {
  display: flex;
  justify-content: center;
}

.right {
  height: 100%;
  width: 45%;
}

.image {
  width: 100%;
  height: 100%;
}

@media (max-width: 600px) {
  .content {
    flex-direction: column;
  }
  .left {
    height: 100%;
    width: 100%;

    padding-top: 2vw;
    padding-bottom: 4vw;
    padding-right: 4vw;
    padding-left: 4vw;
  }
  .para {
    margin-top: 4vw;
    margin-bottom: 4vw;
  }
  .cont-btn {
    display: flex;
    justify-content: start;
  }
  .right {
    height: 100%;
    width: 100%;
    padding: 4vh;
  }
  nav {
    background-color: lightseagreen;
  }
  .nav-items {
    color: white;
  }

  .nav-items h4 {
    display: none;
  }

  h2 {
    color: white;
  }

  .nav-items i {
    font-size: 6vw;
    display: block;
  }

  .button {
    background-color: rgb(109, 184, 216);
    color: black;
    font-size: 1rem;
    padding-top: 1rem;
    padding-bottom: 1rem;
    padding-right: 2.5rem;
    padding-left: 2.5rem;
    border-radius: 10px;
    border: 1px solid black;
  }
}
</style>

<template>
  <div id="main">
    <!--  <div class="parent">
      <div class="child1"></div>
      <div class="child2"></div>
      <div class="child3"></div>
    </div> -->

    <nav>
      <div>
        <h2>LOGO</h2>
      </div>
      <div class="nav-items">
        <h4>Store</h4>
        <h4>Courses</h4>
        <h4>Careers</h4>
        <h4>Blog</h4>
        <h4>Accounts</h4>
        <i class="bi bi-list"></i>
      </div>
    </nav>

    <div class="content">
      <div class="left">
        <h1 class="heading">learning from the <span>coolest</span></h1>
        <p class="para">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Expedita et perferendis autem sunt cumque praesentium totam dignissimos, eos ut, quae, error nesciunt accusamus consequuntur cum dolorum! Nisi, reiciendis porro?</p>
        <div class="cont-btn">
          <button type="button" class="button">Button</button>
        </div>
      </div>
      <div class="right">
        <img src="../assets/graphic2.jpg" class="image" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CSS",
};
</script>
