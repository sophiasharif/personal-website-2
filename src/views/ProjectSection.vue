<template>
  <div class="wrapper">
    <header>
      <h2>Projects</h2>
      <div id="description" >
        <h3 v-if="!mqTablet.matches">
          Here are some of the projects I'm proud of. Click on the link icon to
          see a live demo or on the YouTube icon to see me walk through the
          project!
        </h3>
        <h3 v-else>Tap the cards to navigate!</h3>
      </div>
    </header>
    <div class="card-list">
      <ProjectCard
        class="card"
        v-for="(project, index) in projects"
        :key="project.title"
        :date="project.date"
        :title="project.title"
        :skills="project.skills"
        :description="project.description"
        :demoLink="project.demoLink"
        :youtubeLink="project.youtubeLink"
        :githubLink="project.githubLink"
        :class="project.class"
        :index="index"
        :nCards="projects.length"
        @click="handleClick"
      />
    </div>
  </div>
</template>

<script>
import ProjectCard from "../components/ProjectCard.vue";

export default {
  components: { ProjectCard },
  computed: {
    mqMobile() {
      return window.matchMedia("(max-width: 480px)");
    },
    mqTablet() {
      return window.matchMedia("(max-width: 770px)");
    },
  },
  data() {
    return {
      projects: [
        {
          date: "May 20, 2021",
          title: "Personal Website",
          skills: ["Vue", "Firebase", "JavaScript", "CSS"],
          description:
            "I took this as an opportunity to get creative with CSS and strengthen my Firebase skills!",
          demoLink: "https://www.youtube.com",
          youtubeLink: "youtube.com",
          githubLink: "github.com",
          class: "card",
        },
        {
          date: "May 20, 2021",
          title: "LA Hacks",
          skills: ["React", "JavaScript", "Sass"],
          description:
            "I'm on the Tech team of the largest hackathon in Southern California! I worked with the Design team and created several components throughout the website.",
          demoLink: "https://lahacks.com/",
          walkthroughLink: "youtube.com",
          githubLink: "github.com",
          class: "card",
          index: "2",
        },
        {
          date: "May 20, 2021",
          title: "Poll Data String Processor",
          skills: ["C++"],
          description: "I did this project at part of my CS31 class.",
          demoLink: "sophiasharif.com",
          walkthroughLink: "youtube.com",
          githubLink: "github.com",
          class: "card",
          index: "3",
        },
        {
          date: "May 20, 2021",
          title: "Personal Website version 1",
          skills: ["Python", "Flask", "Bootstrap"],
          description:
            "I focused on the back-end on the first version of this website. I used Flask for the backend and Bootstrap for the front end.",
          demoLink: "sophiasharif.com",
          walkthroughLink: "youtube.com",
          class: "card",
          index: "4",
        },
      ],
    };
  },
  methods: {
    handleClick() {
      if (window.innerWidth <= 1050)
        this.projects.unshift(this.projects.pop());
    },
  },
};
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  height: 100vh;
  justify-content: center;
  align-items: center;
}
header {
  display: flex;
  flex-direction: column;
  align-items: center;
}
header h2 {
  font-size: 2rem;
  margin-top: 0;
}
header h3 {
  margin: 0;
}
header #description {
  max-width: 700px;
  text-align: center;
  margin-bottom: 1rem;
}
header #description h3 {
  font-weight: 400;
}
.card-list {
  display: flex;
  justify-content: center;
  height: 400px;
  margin-bottom: 2rem;
}
/* hover animation for desktop */
@media (min-width: 1050px) {
  .card:hover {
    transform: translateY(-1rem) rotate(3deg);
  }
  .card:hover ~ .card {
    transform: translateX(160px);
  }
  .card:not(:first-child) {
    margin-left: -130px;
  }
}
</style>
