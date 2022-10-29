<template>
  <section id="USP" title="About What The Hack 2022">
    <!-- <svg viewBox="0 0 1440 320" xmlns="http://www.w3.org/2000/svg" style="transform: translateY(-10px);">
      <path
        class="slope"
        d="m0 0v278l22 9c22 10 65 29 109 29s87-19 131-35 87-29 131-22c43 6 87 31 131 44q65 19 131 0c43-13 87-38 130-47 44-10 88-4 131-13 44-10 88-35 131-26 44 10 88 54 131 80 44 26 87 32 131 9 44-22 87-73 109-98l22-26v-182z"
      ></path>
    </svg> -->
    <div class="container">
      <div class="usp">
        <img class="image" src="./free.png" alt="" />
        <div class="text">Completely Free</div>
      </div>
      <div class="usp">
        <img class="image" src="./welcome.png" alt="" />
        <div class="text">All Skill Levels Welcome</div>
      </div>
      <div class="usp">
        <img class="image" src="./prize.png" alt="" />
        <div class="text">$3000 Prize Pool</div>
      </div>
    </div>
  </section>
</template>

<script>
import Para from '@/components/Para.vue';
import SectionHeader from '@/components/SectionHeader.vue';

export default {
  name: 'usp',
};
</script>

<style scoped>
.text {
  font-family: var(--font-primary);
  font-size: clamp(1.5rem, 2vw, 2rem);
  color: var(--color-regular-text);
  text-align: center;
}

#usp {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.image {
  height: 150px;
  width: 150px;
  margin: 0 auto;
  display: flex;
}

.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;
  margin: 0 auto;
  padding: 100px calc(10vw + 20px);
  background-color: var(--slope-body-color);
  transform: translate(0, -2px);
}

@media (--mobile-wide) {
  .container {
    grid-template-columns: repeat(1, 1fr);
  }
}
</style>
