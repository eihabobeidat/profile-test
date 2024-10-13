<template>
  <div class="earlyDays">
    <TitleSection scene="earlyTitle">
      <div class="clouds cloud-1"></div>
      <Pepe v-bind="{ isPlaying }" />
      <div class="clouds cloud-2"></div>
      <div class="clouds cloud-3"></div>
      <Ocean v-bind="{ isPlaying }" />
    </TitleSection>

    <SceneSection id="early-days">
      <TextBlock>
        <p>Looking to break down barriers within your organization?</p>
        <p class="-big">
          <span class="-purple">PROMPTO</span>
        </p>
        <p>
          PROMPTO is designed to enhance employee connections, streamline
          communication, and boost productivity. Adopt, connect, and empower
          your employees to create a seamless, collaborative work environment.
          PROMPTO’s user-friendly platform helps you speed up response times and
          improve internal communication, ensuring your team stays productive
          and connected.
        </p>
      </TextBlock>
    </SceneSection>
    <SceneSection id="early-days2">
      <TextBlock>
        <p class="-big">
          <span class="-purple">Why Choose DELV?</span>
        </p>
        <ul style="list-style-type: none; padding: 0">
          <li style="margin-bottom: 16px">
            <strong>Expertise Across Industries:</strong> From governments to
            big enterprises, everyone trusts DELV. We're kind of a big deal!
          </li>
          <li style="margin-bottom: 16px">
            <strong>Agility and Speed:</strong> Got an idea? We’ll turn it into
            an MVP in 1-2 months. Blink, and it's done!
          </li>
          <li style="margin-bottom: 16px">
            <strong>AI Innovation:</strong> Our AI magic boosts your products
            and helps you make smarter decisions. You're welcome!
          </li>
          <li style="margin-bottom: 16px">
            <strong>The DELV Difference:</strong> We make tech work for you, not
            the other way around. Say goodbye to barriers!
          </li>
          <li style="margin-bottom: 16px">
            <strong>Intelligent Automation & SmartLockers:</strong> From
            automating tasks to SmartLockers, we make life easier for your team.
          </li>
          <li style="margin-bottom: 16px">
            <strong>Partnerships for Growth:</strong> ServiceNow integrations?
            Yep, we do that too. New opportunities are just a click away!
          </li>
          <li style="margin-bottom: 16px">
            <strong>Careers & Internships – Shaping the Future:</strong> Our
            internship program is shaping future innovators. We’re building
            Australia’s next tech leaders!
          </li>
        </ul>
      </TextBlock>
    </SceneSection>
    <SceneSection id="early-days3"> </SceneSection>
  </div>
</template>

<script>
import Pepe from '../Characters/Pepe/Pepe.vue'
import Ocean from '../Characters/Ocean/Ocean.vue'
import TitleSection from '../TitleSection.vue'
import TextBlock from '../TextBlock.vue'
import SceneSection from '../SceneSection.vue'

export default {
  name: 'EarlyDaysScene',
  components: {
    TitleSection,
    Pepe,
    Ocean,
    TextBlock,
    SceneSection,
  },
  props: {
    isPlaying: Boolean,
  },
}
</script>

<style lang="scss">
.earlyDays {
  .pepe {
    position: absolute;
    z-index: 2;
    top: 50%;
    left: 100%;
    transform: scale(0.4) translate3d(0, -50%, 0);
    transform-origin: 0 0;

    @media screen and (max-width: 568px) {
      transform: scale(0.2) translate3d(0, -50%, 0);
    }
  }

  .clouds {
    position: absolute;
    width: 150vw;
    height: 150vh;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    transform-origin: 50% 50%;
    background: url('../Characters/Pepe/assets/clouds-1.png') no-repeat center;
    background-size: contain;
    opacity: 0.5;

    &.cloud-2 {
      background-image: url('../Characters/Pepe/assets/clouds-2.png');
    }

    &.cloud-3 {
      background-image: url('../Characters/Pepe/assets/clouds-3.png');
      width: 100vw;
      height: 100vh;
      z-index: -1;
      opacity: 0.25;
    }
  }
}
</style>
