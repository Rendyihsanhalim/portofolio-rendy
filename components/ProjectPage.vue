<template>
  <section class="overlay">
    <div class="navigation_wrapper">
      <div class="navigation_container">
        <div class="navigation_item" :class="{ 'show-link': showAboutMe }">
          <a class="navigation_link navigation_link1" @click="toggleParagraph('aboutMe')">
            <span data-text="AboutMe">AboutMe</span>
            <div class="hover-content" ref="paragraph" :class="{ 'show__paragraph': showAboutMe, 'slide-in': showAboutMe }">
              <p class="paragraph">This is information about me.</p>
            </div>
          </a>
        </div>
        <div class="navigation_item">
          <a class="navigation_link navigation_link2" @click="toggleParagraph('projects')">
            <span data-text="Projects">Projects</span>
            <div class="hover-content" :class="{ 'show__paragraph': showAboutMe }">
              <p>This is information about my projects.</p>
            </div>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      showAboutMe: false,
      showProjects: false,
      scrollPosition: 0,
    };
  },
  methods: {
    toggleParagraph(section) {
      if (section === 'aboutMe') {
        this.showAboutMe = !this.showAboutMe;
        this.showProjects = false;
      } else if (section === 'projects') {
        this.showProjects = !this.showProjects;
        this.showAboutMe = false;
      }
    },
    handleScroll() {
      console.log("adas")
      this.scrollPosition = window.scrollY || window.scrollTop || document.documentElement.scrollTop;

      const scrollThreshold = 400;

      if (this.scrollPosition > scrollThreshold) {
        this.showAboutMe = false;
        this.showProjects = false;
      }
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

<style>
.overlay {
  width: 100%;
  height: 1000px;
  background-color: rgba(0, 0, 0, 1);
  margin-top: 9rem;
  overflow-x: hidden;
}

.navigation_wrapper {
  margin-top: 100px;
  margin-left: 50px;
  position: absolute;
}

.navigation_container {
  display: flex;
  flex-direction: column;
}

.navigation_link span {
  display: block;
  user-select: none;
  margin: 20px 0;
  font-family: "Fontbaru";
  font-size: 78px; /* Adjusted font size */
}
.hover-content p{
  font-size:2.5rem;
  font-family: "Montserrat";
}

.navigation_link {
  color: rgba(255, 255, 255, 0.3);
  position: relative;
  display: inline-block;
  transition: margin-bottom 0.3s ease; /* Added transition for smooth effect */
}

.show-link {
  margin-bottom: 10rem;
}

.show__paragraph{
    left:0;
}

.hover-content {
  position: absolute;
  top: 100%;
  left: -1000%;
  background-color: rgba(0, 0, 0, 0.8);
  color: white;
  padding: 10px;
  width: 500px;
  border-radius: 5px;
  transition: left 1s;
}


.slide-in {
  left: 0;
  transform: translateX(100%); /* Initial position off-screen to the right */
}

.show__paragraph {
  display: block;
}

.navigation_wrapper span:before {
  width: 0;
  color: white;
  overflow: hidden;
  position: absolute;
  content: attr(data-text);
  transition: all 1s cubic-bezier(0.84, 0, 0.08, 0.99);
}

.navigation_wrapper span:hover:before {
  width: 100%;
}

.project-preview-wrapper {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  position: fixed;
}
</style>
