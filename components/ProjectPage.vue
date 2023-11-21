<template>
  <section class="overlay">
    <div class="navigation_wrapper">
      <div class="project-preview-wrapper">
        <div class="project-wrapper">
          <!-- Add a paragraph for AboutMe content -->
          <p class="about-me-paragraph">Your AboutMe content goes here...</p>
        </div>
      </div>
      <ul class="navigation_list">
        <li class="navigation_item">
          <a class="navigation_link navigation_link1">
            <span data-text="AboutMe">AboutMe</span>
          </a>
        </li>
        <li class="navigation_item">
          <a class="navigation_link navigation_link2">
            <span data-text="Projects">Projects</span>
          </a>
        </li>
      </ul>
    </div>
  </section>
</template>

<style>
.overlay {
  width: 100%;
  height: 1000px;
  background-color: rgba(0, 0, 0, 1);
  margin-top: 9rem;
  overflow-x: hidden;
}

.navigation_wrapper ul {
  margin-top: 100px;
  margin-left: 50px;
  list-style: none;
  position: absolute;
}

.navigation_item {
  display: block;
  user-select: none;
  margin: 120px 0;
  font-family: "Fontbaru";
  font-size: 74px;
}

.navigation_link {
  color: rgba(255, 255, 255, 0.3);
}

.about-me-paragraph {
  opacity: 0; /* Initially set opacity to 0 */
  color: white;
  font-size: 18px;
  margin-top: 10px;
  transition: opacity 0.5s;
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

.projection-wrapper {
  position: absolute;
  top: 12%;
  left: 50%;
  width: 0;
  height: 400px;
  background: url() no-repeat 50% 50%;
  background-size: cover;
  overflow-x: hidden;
}
</style>

<script>
// Import GSAP
const { gsap } = window;

// GSAP animation for AboutMe paragraph
const aboutMeParagraph = document.querySelector('.about-me-paragraph');

gsap.to(aboutMeParagraph, {
  opacity: 1, // Set opacity to 1 on hover
  paused: true, // Animation initially paused
  duration: 0.5, // Animation duration
});

// Hover event for "AboutMe" link
const aboutMeLink = document.querySelector('.navigation_link1');

aboutMeLink.addEventListener('mouseenter', () => {
  gsap.resume(); // Resume GSAP animation
});

aboutMeLink.addEventListener('mouseleave', () => {
  gsap.pause(); // Pause GSAP animation
});
</script>
