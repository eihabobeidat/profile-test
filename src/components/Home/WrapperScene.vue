<template>
  <SceneSection class="scene" id="wrapperTitle">
    <h1 class="title">Careers & Internships</h1>
    <p>
      Shaping the Future At DELV, we believe in giving back to the community.
      Our Industry-Leading Internship Program equips students with employability
      skills and real-world experience. Launched initially with the University
      of Canberra, we’ve expanded this program to offer more students across
      Australia the opportunity to work alongside industry experts and gain
      practical insights into the tech industry. We don’t just hire talent; we
      nurture it, ensuring that the innovators of tomorrow are empowered to make
      their mark on the industry. By investing in future talent, we’re building
      a stronger, more innovative Australia.
    </p>
  </SceneSection>
</template>

<script>
import SceneSection from '../SceneSection.vue'

export default {
  name: 'WrapperBlock',
  components: { SceneSection },
}
</script>

<style lang="scss">
#wrapperTitle {
  .title {
    color: var(--purple);
  }

  .std {
    font-size: 1rem;
  }

  .-answer {
    opacity: 0.6;
  }
}
</style>
