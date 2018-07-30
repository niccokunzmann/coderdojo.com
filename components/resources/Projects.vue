<template>
  <div class="c-projects center-text">
    <h1>{{ $t('Projects for your Dojo') }}</h1>
    <div class="c-projects__cards">
      <a :href="projectsUrl" class="c-projects__card" v-for="(project, i) in projects" :key="i">
        <img :src="project.imgSrc" />
        <h3>{{ $t(project.title) }}</h3>
      </a>
    </div>
    <div class="c-projects__cta">
      <a :href="projectsUrl" class="c-button c-button--orange">{{ $t('View more CoderDojo projects') }}</a>
    </div>
    <div class="c-projects__discuss">
      <p>{{ $t('If you have produced a piece of original content for your Dojo, or found a useful resource online that you think others might find useful, please contribute it to the collection!') }}</p>
      <a href="https://forums.coderdojo.com/">{{ $t('Discuss your content on our forums') }}</a>
    </div>
  </div>
</template>

<script>
  import projects from '~/data/resources/projects';
  export default {
    data() {
      return {
        projects,
      };
    },
    computed: {
      locale: function () {
        return this.$store.state.locale;
      },
      projectsUrl: function () {
        return `https://projects.raspberrypi.org/${this.locale}/coderdojo`
      },
    },
  };
</script>


<style lang="scss" scoped>
  @import '~/assets/_variables.scss';

  .c-projects {
    &__cards {
      display: flex;
      margin: 40px auto;
      flex-wrap: wrap;
    }

    &__card {
      flex: 1;
      background: $white;
      color: $black;
      border-radius: 5px;
      margin: 0 15px;
      width: 30%;
      text-decoration: none;

      img {
        width: 100%;
      }

      h3 {
        text-transform: uppercase;
        margin: 20px;
      }

      p {
        margin: 5px 20px 20px 20px;
        text-align: center;
      }
    }

    &__cta {
      text-align: center;
      margin: 40px 0;
    }

    &__discuss {
      text-align: center;
        font-size: 18px;

      p {
        max-width: 605px;
        margin: 80px auto 40px;
      }

      a {
        display: block;
        color: $cd-orange;
        font-weight: bold;
        text-decoration: underline;
        margin: 40px 0;
      }
    }
  }
  @include media-breakpoint-max(sm) {
    .c-projects {
      &__cards {
        flex-direction: column;
      }
      &__card {
        width: auto;
        margin-right: 45px;
        margin-left: 45px;
        margin-bottom: 30px;
      }
      &__discuss {
        margin: 0 20px;
      }
    }
  }
</style>