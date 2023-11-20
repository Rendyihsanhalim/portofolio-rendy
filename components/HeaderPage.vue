<template>
    <header class="header"  id="header">
      <nav class="nav container">
        <a class="nav__logo">
            PORTOFOLIO
        </a>
  
        <div class="nav__menu" :class="{ 'show-menu': isMenuVisible }">
          <ul class="nav__list">
            <li class="nav__item">
              <nuxt-link to="/" class="nav__link">Home</nuxt-link>
            </li>
            <li class="nav__item">
              <a to="/Product" class="nav__link">Product</a>
            </li>
            <li class="nav__item">
              <a class="nav__link">Inspiration</a>
            </li>
            <li class="nav__item">
              <a class="nav__link">About Us</a>
            </li>
          </ul>
          

          <!-- CLOSE BUTTON -->
          <div class="nav__close" @click="hideMenu" id="nav-close">
            <i class="fa-solid fa-xmark"></i>
          </div>
        </div>
  
        <!-- TOGGLE BUTTON -->
        <div class="nav__toggle" @click="toggleMenu" id="nav-toggle">
          <i class="fa-solid fa-bars"></i>
        </div>
        
      </nav>
    </header>
  </template>
  

  
  <script>

  export default {
    data() {
      return {
        isMenuVisible: false,

      };
    },
    methods: {
      toggleMenu() {
        this.isMenuVisible = !this.isMenuVisible;
      },
      hideMenu() {
        this.isMenuVisible = false;
      },

      

      },
    mounted() {
      window.addEventListener('scroll', this.handleScroll);

    },
    beforeDestroy() {
      window.removeEventListener('scroll', this.handleScroll);
    },
  };
  </script>
  
  
  
  <style scoped>
  .container {
      max-width: 1122px;
      margin-inline: 2.25rem;
  }
  
  .grid {
      display: grid;
  }
  


  
  /*=============== HEADER & NAV ===============*/
  .header {
      width: 100%;
      top: 0;
      left: 0;
      z-index: 100;
      transition: box-shadow .4s;

  }
  
  
  .nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 3.5rem;
      font-size: 1rem;
      font-family: "Montserrat";
  }
  
  .nav__menu{
    z-index:1000;
  }
  .nav__toggle,.nav__close {
      display: flex;
      font-size: 1.25rem;
      color: black;
      cursor: pointer;
  }
  
  /* Navigation for mobile devices */
  @media screen and (max-width:1023px) {
      .nav__menu {
          width: 80%;
          position: fixed;
          top: 0;
          right: -100%;
          background-color: rgb(255, 255, 255);
          box-shadow: -1px 0 16px hsla(0, 0%, 0%, .1);
          height: 100%;
          padding: 6rem 3rem;
          transition: right .4s;
          text-align: center;
          z-index:1000;
          height:100vh;

      }
  
  }
  
  .nav__list {
      display: flex;
      flex-direction: column;
      row-gap: 2.5rem;
  }
  
  .nav__link {
      color: black;
      font-family: "Montserrat";
      text-decoration:none;
  }
  
  
  .nav__close {
      position: absolute;
      top: 1.125rem;
      right: 1.5rem;
      color: var(--title-color);
  }
  
  .nav__link {
  position: relative;
  transition: color 0.3s, transform 0.3s;
}

.nav__link:hover {
  color: rgb(105, 97, 97); /* Ganti warna sesuai keinginan Anda */
  transform: scale(1.5); /* Ganti skala sesuai keinginan Anda */
}

.nav__toggle:hover,
.nav__close:hover {
  transform:scale(1.5); /* Ganti warna sesuai keinginan Anda */
}

/* Animasi */
.nav__link::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: grey; /* Ganti warna sesuai keinginan Anda */
  transform-origin: bottom right;
  transform: scale(0, 1);
  transition: transform 0.3s ease-out;
}

.nav__link:hover::before {
  transform-origin: bottom left;
  transform: scale(1, 1);
}
  
  /* Show menu */
  .show-menu {
      right: 0;
      z-index: 100;
  }
  
  /* Add shadow header */
  .shadow-header {
      box-shadow: 0 1px 16px hsla(0, 0%, 0%, .1);
  }
    /*=============== BREAKPOINTS ===============*/
  /* For small devices */
  
  @media screen and (max-width:320px) {
    .container{
      margin-inline: 0.5rem;
    }
  }

  
  /* For large devices */
  @media screen and (min-width:1023px){
    .nav{
      height: calc(3.5rem+ 2rem);
      width: 100%;
      margin-inline:3rem;
      gap:1.75rem;
    }
  
    .nav__toggle,.nav__close{
      display: none;
    }
    .nav__menu{
      display: flex;
      justify-content: space-between;
      align-items: center
    }
   .nav__list{
    flex-direction: row;
    column-gap: 4rem;
   }
  }
  </style>