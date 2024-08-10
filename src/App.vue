<template>
  <div class="layer"></div>
  <nav>
    <div class="logo">{{ name }}</div>
    <div
      class="container"
      aria-checked="unclicked"
      id="btn"
      @click="clickedNav()"
    >
      <div class="small-nav-1" id="btn1"></div>
      <div class="small-nav-2" id="btn2"></div>
      <div class="small-nav-3" id="btn3"></div>
    </div>
    <div class="links">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
      <router-link to="/portfolio">Portfolio</router-link>
      <router-link to="/contact">Contact</router-link>
    </div>

    <!-- small nav bar -->
    <div class="links-small-nav" id="small-nav">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
      <router-link to="/portfolio">Portfolio</router-link>
      <router-link to="/contact">Contact</router-link>
    </div>
  </nav>
  <router-view />
</template>

<style lang="scss">
#app {
  //font-family: Avenir, Helvetica, Arial, sans-serif;
  font-family: "Ubuntu", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #20356e;
  position: relative;
  overflow: hidden;
}

// animtion
@keyframes zooming {
  0% {
    transform: scale(1);
  }

  100% {
    transform: scale(1.7);
  }
}

nav {
  padding: 1rem;
  height: 3rem;
  display: flex;
  justify-content: space-between;
  padding: 1rem 2rem;
  align-items: center;
  overflow: hidden;
  @media (max-width: 1050px) {
    justify-content: space-between;
  }

  //small navigation bar
  .container {
    display: none;
    position: relative;
    height: 1.25rem;
    cursor: pointer;
    @media (max-width: 1050px) {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
      transition: all 0.3s ease;
    }
    @media (max-width: 300px) {
      height: 1rem;
    }
    .small-nav-1 {
      width: 2rem;
      height: 0.25rem;
      border-radius: 1rem;
      background-color: #253c59;
      transition: all 0.3s ease;
      @media (max-width: 300px) {
        width: 1.25rem;
        height: 0.2rem;
      }
    }
    .small-nav-2 {
      width: 2rem;
      height: 0.25rem;
      border-radius: 1rem;
      background-color: #253c59;
      transition: all 0.3s ease;
      @media (max-width: 300px) {
        width: 1.25rem;
        height: 0.2rem;
      }
    }
    .small-nav-3 {
      width: 2rem;
      height: 0.25rem;
      border-radius: 1rem;
      background-color: #253c59;
      transition: all 0.3s ease;
      @media (max-width: 300px) {
        width: 1.25rem;
        height: 0.2rem;
      }
    }
  }

  .logo {
    font-size: 1.5rem;
    font-weight: bold;
    @media (max-width: 300px) {
      font-size: 1rem;
    }
  }

  .links {
    width: 50vw;
    display: flex;
    justify-content: space-around;
    align-items: center;
    @media (max-width: 1050px) {
      display: none;
    }
  }

  #btn {
    position: relative;
    z-index: 7;
  }
  .links-small-nav {
    display: none;
    transition: all 0.3s ease-out;
    position: absolute;
    @media (max-width: 1050px) {
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      align-items: center;
      gap: 2rem;
      padding: 3rem 6rem 1rem 3rem;
      border-radius: 1rem;
      background-color: white;
      box-shadow: 1px 1px 16px 1px #ddd;
      z-index: 6;
      top: 1rem;
      right: 0;
      transform: translateX(100%);
    }
  }

  a {
    font-weight: bold;
    color: #20356e;
    padding: 0.5rem 2rem;
    transition: 0.2s ease-in-out;

    &:hover {
      color: white;
      background-color: #20356e;
      padding: 0.5rem 2rem;
    }

    &.router-link-exact-active {
      color: white;
      background-color: #20356e;
      padding: 0.5rem 2rem;
    }
  }
}
</style>

<script>
export default {
  data: function () {
    return {
      name: "Mohammed Saeed",
    };
  },
  methods: {
    clickedNav: function () {
      let btn = document.getElementById("btn");
      let btn1 = document.getElementById("btn1");
      let btn2 = document.getElementById("btn2");
      let btn3 = document.getElementById("btn3");
      let smallNav = document.getElementById("small-nav");
      let elementWidth;

      smallNav.onclick = () => {
        btn.ariaChecked = "unclicked";
        btn1.style.transform = "translateX(0)";
        btn2.style.display = "block";
        btn3.style.transform = "translateX(0)";
        smallNav.style.transform = "translateX(100%)";
      };
      if (window.outerWidth < 300) {
        elementWidth = "6.5px";
      } else {
        elementWidth = "8px";
      }

      if (btn.ariaChecked === "clicked") {
        btn.ariaChecked = "unclicked";
        btn1.style.transform = "translateX(0)";
        btn2.style.display = "block";
        btn3.style.transform = "translateX(0)";
        smallNav.style.transform = "translateX(100%)";
      } else if (btn.ariaChecked === "unclicked") {
        btn.ariaChecked = "clicked";
        btn1.style.transform = `translateY(${elementWidth}) rotate(-45grad)`;
        btn2.style.display = "none";
        btn3.style.transform = `translateY(-${elementWidth}) rotate(45grad)`;
        smallNav.style.transform = "translateX(0)";
      }
    },
  },
};
</script>
