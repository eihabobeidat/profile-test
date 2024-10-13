<template>
  <div>
    <div class="pepe bg-head">
      <div class="blink"></div>
      <div class="keyboard"></div>
      <div class="minas"></div>
      <div class="rio">
        <div class="particles"></div>
        <div class="vase">
          <div class="bg-rio_vase_foliage_3"></div>
          <div class="bg-rio_vase_foliage_2"></div>
          <div class="bg-rio_vase_foliage_1"></div>
          <div class="bg-rio_vase"></div>
        </div>
        <div class="bg-rio_pao_cristo"></div>

        <div class="waterfall"></div>

        <div class="bg-rio_palmtree_1"></div>
        <div class="bg-rio_palmtree_2"></div>
      </div>
      <div class="am-pa">
        <div class="bg-ampa_foliage_3"></div>
        <div class="bg-ampa_tree_2"></div>
        <div class="bg-ampa_foliage_2"></div>
        <div class="bg-ampa_parrot_wing"></div>
        <div class="bg-ampa_foliage_1"></div>
        <div class="bg-ampa_ver_o_peso"></div>
        <div class="bg-ampa_tree_1"></div>
        <div class="bg-ampa_oxes"></div>
      </div>
      <div class="metals">
        <div class="bg-metals_sax"></div>
        <div class="bg-metals_trumpet"></div>
        <div class="bg-metals_trombone">
          <div class="bg-metals_trombone_thing"></div>
        </div>
      </div>

      <div class="bonfim-church"></div>
      <div class="bonfim b1"></div>

      <div class="ear bg-head-ear"></div>
    </div>
  </div>
</template>

<script>
import { TimelineMax } from 'gsap'
import { random } from '@/utils'
import { character } from '../character.mixin'
import {
  LOOP,
  LOOP_EASE_IN_OUT,
  LOOP_EASE_OUT,
  LOOP_ELASTIC_OUT,
} from '../../../constants'

export default {
  name: 'PepeCharacter',
  mixins: [character],
  data() {
    return {
      particlesLoops: [],
    }
  },
  methods: {
    initParticles() {
      if (this.$viewport.isMobile) return

      const particlesCount = this.$viewport.isTablet ? 10 : 15
      const particles = document.querySelector('.pepe .particles')

      if (!particles) return

      for (let i = 0, particle; i < particlesCount; i++) {
        particle = document.createElement('div')
        particle.className = `particle p${i}`
        particles.appendChild(particle)

        this.particlesLoops[i] = new TimelineMax()
        this.particlesLoops[i]
          .delay(random(0, 7))
          .to(`.particle.p${i}`, random(3, 5), {
            y: random(100, 1000),
            x: random(100, 500),
            rotationY: 360 * random(5, 20),
            rotationZ: 360 * random(5, 20),
            autoAlpha: 0,
            repeat: -1,
          })
      }
    },
    init() {
      this.initParticles()

      // head
      const ampa_parrot = document.querySelector('.bg-ampa_parrot_wing')
      const metal_sax = document.querySelector('.bg-metals_sax')
      const metal_trumpet = document.querySelector('.bg-metals_trumpet')
      const metal_trombone = document.querySelector('.bg-metals_trombone')
      const metal_trombone_thing = document.querySelector(
        '.bg-metals_trombone_thing'
      )
      const pepe = document.querySelector('.pepe')
      const blink = document.querySelector('.pepe .blink')
      const ear = document.querySelector('.bg-head-ear')
      const rhythm = 0.3

      this.loop
        .addLabel('start', 0)
        // pepe
        .fromTo(
          blink,
          0.2,
          {
            autoAlpha: 1,
          },
          {
            autoAlpha: 0,
            repeat: -1,
            repeatDelay: random(1, 2.5),
          },
          'start'
        )

      if (!this.$viewport.isMobile) {
        this.loop
          // metals
          .to(
            metal_sax,
            rhythm,
            {
              transformOrigin: '25% 10%',
              yPercent: random(-10, 0),
              rotation: random(-5, 6),
              ...LOOP,
            },
            'start'
          )
          .to(
            metal_trumpet,
            rhythm * 2,
            {
              transformOrigin: '30% 100%',
              rotation: random(-20, 25),
              yPercent: 10,
              ...LOOP_EASE_OUT,
            },
            'start'
          )
          .to(
            metal_trombone,
            rhythm * 4,
            {
              transformOrigin: '0% 100%',
              rotation: random(-40, 45),
              yPercent: 10,
              ...LOOP_EASE_IN_OUT,
            },
            'start'
          )
          .to(
            metal_trombone_thing,
            rhythm / 2,
            {
              transformOrigin: '0% 0%',
              xPercent: random(-25, 15),
              ...LOOP,
            },
            'start'
          )
      }

      if (this.$viewport.isDesktop) {
        this.loop
          // parrot
          .to(
            ampa_parrot,
            1,
            {
              transformOrigin: '0% 0%',
              rotation: random(-5, 5),
              xPercent: random(-5, 0),
              yPercent: random(0, 5),
              ...LOOP_ELASTIC_OUT,
            },
            'start'
          )
          // pepe
          .to(
            ear,
            rhythm,
            {
              transformOrigin: '40% 50%',
              rotationY: random(5, 15),
              ...LOOP,
            },
            'start'
          )
          .to(
            pepe,
            3,
            {
              yPercent: random(-3, 3),
              ...LOOP_EASE_IN_OUT,
            },
            'start'
          )
      }
    },
    toggleGsapAnimations(isPlaying) {
      if (isPlaying) {
        this.$el.classList.remove('animationStop')
        this.loop.play()
        this.particlesLoops.forEach((loop) => loop.play())
      } else {
        this.$el.classList.add('animationStop')
        this.loop.stop()
        this.particlesLoops.forEach((loop) => loop.stop())
      }
    },
  },
}
</script>

<style lang="scss"></style>
