<template>
  <section class="home" id="home" ref="homeSection">
    <div class="home__container">

      <div class="home__text">
        <h1 class="home__h1">RENDY</h1>
        <p class="home__paragraph">
          I'm Junior FrontEnd Developer Who Addicted make beautiful website
        </p>
        <a class="button__home button_flex">
          Learn More <i class="fa-solid fa-arrow-right button__icon"></i>
        </a>
      </div>

      <div class="home__circle">
        <img src="~assets/img/circle1.png" alt="" class="home__circle1">
        <img src="~assets/img/circle2.png" alt="" class="home__circle2">
        <img src="~assets/img/circle1.png" alt="" class="home__circle3" ref="homeCircle3">
      </div>


    </div>
  </section>
</template>

<script type="module">
export default {
  data() {
    return {
    };
  },
  methods: {
    setupScrollTrigger() {
      this.$gsap.registerPlugin(this.$ScrollTrigger);


      this.$gsap.to('.overlay', {
        y: -500,
        duration: 3,
        scrollTrigger: {
          trigger: '.home__circle3',
          start: 'top 60%',
          end: 'bottom 40%',
          scrub: true,
        },
      });




      if (window.innerHeight < 950) {
        this.$gsap.to('.home__text', {
          y: -200,
          opacity: 0,
          duration: 1,
          scrollTrigger: {
            trigger: '.home__circle3',
            start: 'top 65%',
            end: 'top 40%',
            scrub: true,
          },
        });

        this.$gsap.to('.home__circle2', {
          x: 1500,
          scale: 0.25,
          duration: 10,
          scrollTrigger: {
            trigger: '.home__circle3',
            start: 'top 65%',
            end: 'top 30%',
            scrub: true,
          },
        });

        this.$gsap.to('.home__circle1', {
          x: -1500,
          scale: 1.5,
          duration: 10,
          scrollTrigger: {
            trigger: '.home__circle3',
            start: 'top 65%',
            end: 'top 30%',
            scrub: true,
          },
        });

      };

      if (window.innerHeight > 950 && window.innerHeight < 1179) {
        this.$gsap.to('.home__text', {
          y: -200,
          opacity: 0,
          duration: 1,
          scrollTrigger: {
            trigger: '.home__circle3',
            start: 'top 35%',
            end: 'top 50%',
            scrub: true,
          },
        })
      };

      if (window.innerHeight > 1179) {
        this.$gsap.to('.home__text', {
          y: -200,
          opacity: 0,
          duration: 1,
          scrollTrigger: {
            trigger: '.home__circle3',
            start: 'top 55%',
            end: 'top 80%',
            scrub: true,
          },
        })
      };
    },
  },
  mounted() {
    this.setupScrollTrigger();
  },
};
</script>

<style>
/* ... Style yang ada sebelumnya ... */
.home {
  margin-inline: 3rem;
  margin-top: 4rem;
  position: relative;
}

.home__container {
  margin: 0 auto;
  text-align: center;
}

.home__text {
  font-family: "Fontbaru";
  text-align: center;
}

.home__h1 {
  font-weight: 600;
  font-size: 5rem;
  margin-bottom: 1.5rem;
}

.home__paragraph {
  font-weight: 400;
  font-size: 2rem;
  margin-bottom: 1rem;
  font-family: "Montserrat";
}

.home__circle {
  position: relative;
  width: 100%;
}

.home__circle1 {
  position: absolute;
  bottom: 3rem;
  right: 2rem;
  width: 300px;
  z-index: -1;
}

.home__circle2 {
  position: absolute;
  bottom: -6rem;
  left: -2rem;
  width: 350px;
  z-index: -1;
}

.home__circle3 {
  position: absolute;
  top: 3rem;
  right: 10rem;
  width: 500px;
}

.button__home {
  display: inline-block;
  background-color: rgb(29, 29, 49);
  color: white;
  padding: 1rem 1.75rem;
  border-radius: .5rem;
  font-weight: 400;
  transition: .3s;
  cursor: pointer;
}

.button__home:hover {
  background-color: rgb(21, 21, 68)
}

.button__icon {
  transition: .3s;
}

.button__home:hover .button__icon {
  transform: translateX(.5rem);
}

.button_flex {
  display: inline-flex;
  align-items: center;
  column-gap: .5rem;
}


/*=============== BREAKPOINTS ===============*/
/* For small devices */

@media screen and (max-width: 320px) {
  .home {
    margin-inline: 1.5rem;
    height: 100vh;
  }

  .home__circle1 {
    bottom: 9rem;
    right: -1.5rem;
    width: 100px;
    z-index: -1;
  }

  .home__circle2 {
    bottom: -8rem;
    left: -3rem;
    width: 200px;
    z-index: -1;
  }

  .home__circle3 {
    top: 10rem;
    right: -1rem;
    width: 200px;

  }

  .home__h1 {
    font-weight: 600;
    font-size: 2.5rem;
    margin-bottom: 1.5rem;
  }

  .home__paragraph {
    font-weight: 400;
    font-size: 0.98rem;
    margin-bottom: 1rem;
    font-family: "Montserrat";
  }


}

@media screen and (max-width: 576px) {

  .home__circle1 {
    bottom: 9rem;
    right: -1.5rem;
    width: 100px;
    z-index: -1;
  }

  .home__circle2 {
    bottom: -8rem;
    left: -3rem;
    width: 200px;
    z-index: -1;
  }

  .home__circle3 {
    top: 12rem;
    right: -1rem;
    width: 200px;

  }

  .home__h1 {
    font-weight: 600;
    font-size: 3rem;
    margin-bottom: 1.5rem;
  }

  .home__paragraph {
    font-weight: 400;
    font-size: 1.2rem;
    margin-bottom: 1rem;
    font-family: "Montserrat";
  }
}

@media screen and (max-width: 768px) {
  .home__circle1 {
    bottom: 8rem;
    right: -1.5rem;

  }

  .home__circle2 {
    bottom: -12rem;
    left: -4rem;
  }

  .home__circle3 {
    top: 18rem;
    right: -1rem;
    width: 400px;
    /* Styles for screens with a minimum height of 800px and maximum height of 932px */
  }
}

@media screen and (min-width: 769px) {

  .home__circle1 {
    bottom: 8rem;
    right: -1.5rem;

  }

  .home__circle2 {
    bottom: -12rem;
    left: -4rem;
  }

  .home__text {
    opacity: 1;
  }
}

@media screen and (min-width:912px) {
  home {
    margin-top: 15rem;
  }

}

@media screen and (min-height: 800px) and (max-height: 950px) {
  .home__circle3 {
    top: 18rem;
    right: -1rem;
    width: 200px;
    /* Styles for screens with a minimum height of 800px and maximum height of 932px */
  }
}

@media screen and (min-height: 950px) and (max-height: 1025px) {
  .home__circle3 {
    top: 16rem;
    right: -1rem;
    width: 400px;
    /* Styles for screens with a minimum height of 800px and maximum height of 932px */
  }
}

@media screen and (min-height: 1025px) {
  .home__circle3 {
    top: 16rem;
    right: -1rem;
    width: 400px;
    /* Styles for screens with a minimum height of 800px and maximum height of 932px */
  }
}
</style>
