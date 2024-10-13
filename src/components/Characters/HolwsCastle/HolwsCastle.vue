<template>
  <div>
    <div class="castle-container" role="img" aria-labelledby="castleDesc">
      <p class="ariaLabel" id="castleDesc">
        The castle of Howl's movie Moving Castle, flying over a green lawn and a
        blue sky.
      </p>
      <div class="castle">
        <div class="top">
          <div class="top-tower"></div>
          <div class="top-clothes"></div>
          <div class="top-top"></div>
        </div>
        <div class="bucket"></div>
        <div class="mouth">
          <div class="back-lip"></div>
          <div class="front-lip"></div>
        </div>
        <div class="l-leg"></div>
        <div class="r-leg"></div>
        <div class="l-arm"></div>
        <div class="body"></div>
        <div class="fans">
          <div class="fan2"></div>
          <div class="fan1"></div>
          <div class="fix-tail"></div>
        </div>
        <div class="r-arm-holder">
          <div class="r-arm"></div>
          <div class="fix-shoulder"></div>
        </div>
        <div class="ear"></div>
        <div class="lower-foliage">
          <div class="foliage2"></div>
          <div class="foliage1"></div>
          <div class="fix-balcony"></div>
        </div>
        <div class="wing"></div>
        <div class="higher-foliage">
          <div class="foliage3"></div>
          <div class="foliage2"></div>
          <div class="foliage1"></div>
          <div class="fix-roof"></div>
        </div>
        <div class="flag"></div>
      </div>
    </div>
  </div>
</template>

<script>
import { RoughEase, Power0 } from 'gsap'
import { LOOP_EASE_IN_OUT, LOOP } from '@/constants'
import { getNodes } from '@/utils'
import { character } from '../character.mixin'

export default {
  name: 'HolwsCastleCharacter',
  mixins: [character],
  methods: {
    init() {
      const castle = getNodes('.castle')

      this.loop
        .addLabel('start', 0)
        .to(
          castle.topTower,
          2,
          {
            rotation: -15,
            transformOrigin: '50% 100%',
            ease: RoughEase.ease.config({
              template: Power0.easeNone,
              strength: 0.5,
              points: 10,
              taper: 'none',
              randomize: true,
              clamp: false,
            }),
            ...LOOP,
          },
          'start'
        )
        .to(
          castle.bucket,
          0.6,
          {
            rotationZ: -25,
            rotationX: -45,
            transformOrigin: '50% 0%',
            ...LOOP,
          },
          'start'
        )
        .to(
          [castle.frontLip, castle.backLip],
          1.6,
          {
            rotation: -20,
            xPercent: -5,
            transformOrigin: '100% 0%',
            ease: RoughEase.ease.config({
              template: Power0.easeNone,
              strength: 1,
              points: 16,
              taper: 'none',
              randomize: true,
              clamp: false,
            }),
            ...LOOP,
          },
          'start'
        )
        .to(
          castle.ear,
          2,
          {
            rotation: -25,
            transformOrigin: '25% 50%',
            ease: RoughEase.ease.config({
              template: Power0.easeNone,
              strength: 1,
              points: 16,
              taper: 'none',
              randomize: true,
              clamp: false,
            }),
            ...LOOP,
          },
          'start'
        )
        .to(
          castle,
          1.6,
          {
            yPercent: -5,
            ...LOOP_EASE_IN_OUT,
          },
          'start'
        )

      if (this.$viewport.isDesktop) {
        this.loop
          .to(
            castle.topTower,
            2,
            {
              rotation: -15,
              transformOrigin: '50% 100%',
              ease: RoughEase.ease.config({
                template: Power0.easeNone,
                strength: 0.5,
                points: 10,
                taper: 'none',
                randomize: true,
                clamp: false,
              }),
              ...LOOP,
            },
            'start'
          )
          .to(
            castle.lLeg,
            2,
            {
              rotation: -15,
              transformOrigin: '0% 0%',
              ...LOOP_EASE_IN_OUT,
            },
            'start'
          )
          .to(
            castle.rLeg,
            2.2,
            {
              rotation: -15,
              transformOrigin: '0% 0%',
              ...LOOP_EASE_IN_OUT,
            },
            'start'
          )
          .to(
            castle.rArm,
            1.8,
            {
              rotation: 15,
              transformOrigin: '0% 0%',
              ...LOOP_EASE_IN_OUT,
            },
            'start'
          )
          .to(
            castle.lArm,
            2,
            {
              rotation: 15,
              transformOrigin: '0% 0%',
              ...LOOP_EASE_IN_OUT,
            },
            'start'
          )
          .to(
            castle.foliage1,
            0.7,
            {
              transformOrigin: '50% 100%',
              skewX: 10,
              ...LOOP,
            },
            'start'
          )
          .to(
            castle.foliage2,
            0.6,
            {
              transformOrigin: '50% 100%',
              skewX: -8,
              ...LOOP,
            },
            'start'
          )
          .to(
            castle.foliage3,
            0.5,
            {
              transformOrigin: '50% 100%',
              skewX: 6,
              ...LOOP,
            },
            'start'
          )
      }
    },
  },
}
</script>

<style lang="scss"></style>
