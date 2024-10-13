<template>
  <section class="scene-intro" id="intro">
    <div class="static-container">
      <h1 class="title">
        <span class="iuri">Delv </span>
      </h1>

      <TextBlock>
        <p class="-purple">We’re all about innovation</p>
        <p class="-gray">
          Welcome to DELV, Australia’s tech innovator in AI, mobility, and
          cutting-edge solutions. We help businesses transform, empowering teams
          and unlocking new possibilities.
        </p>
      </TextBlock>
    </div>
  </section>
</template>

<script>
import TextBlock from '../TextBlock.vue'

export default {
  name: 'IntroScene',
  components: { TextBlock },
}
</script>
