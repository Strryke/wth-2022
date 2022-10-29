<template>
  <div class="hero-content">
    <div class="icon-wrapper">
      <WTHIcon />
      <div class="cloud-icon-wrapper">
        <CloudIcon />
      </div>
    </div>
    <div class="center">
      <h1>A Brighter Future</h1>
      <div class="hero-content-secondary">
        <div>
          <h2>19th - 20th December 2022</h2>
          <h2>Singapore University of Technology and Design</h2>
        </div>
        <a href="https://sutdwth21.devpost.com/project-gallery" class="register-button">View Submissions</a>
      </div>
    </div>
    <RegistrationGuideModal />
  </div>
</template>

<script>
import openModalMixin from '@/mixins/openModalMixin';
import WTHIcon from '@/sections/hero/WTHIcon';
import CloudIcon from '@/sections/hero/CloudIcon';

export default {
  name: 'hero-content',
  components: {
    RegistrationGuideModal: () => import(/* webpackPrefetch: true */ '@/content-modals/RegistrationGuideModal'),
    WTHIcon,
    CloudIcon,
  },
  mixins: [openModalMixin],
};
</script>

<style scoped>
.hero-content {
  position: relative;
  height: 87.5%;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.center {
  margin: 0 auto;
  margin-top: 40px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.hero-content > .icon-wrapper {
  width: calc(400px + 28vw);
  margin-bottom: 20px;
  position: relative;
  margin: 0 auto;
}

.cloud-icon-wrapper {
  position: absolute;
  top: 0;
  right: -100px;
  width: 10vw;
}

.hero-content h1 {
  font-family: var(--font-secondary), sans-serif;
  font-size: calc(3vw + 14px);
  font-weight: 900;
  color: var(--color-title-text);
  margin-bottom: 8px;
  transition: color 0.6s ease-out;
}

.hero-content-secondary {
  display: flex;
  flex-direction: column;
}

.hero-content h2 {
  font-family: var(--font-primary), sans-serif;
  font-size: calc(1vw + 10px);
  font-weight: 400;
  color: var(--color-title-text);
  transition: color 0.6s ease-out;
}

.register-button {
  display: block;
  border-radius: 10px;
  align-items: center;
  text-decoration: none;
  font-size: 24px;
  font-family: var(--font-secondary), sans-serif;
  font-weight: 700;
  background-color: var(--color-title-text);
  color: var(--color-cta-text);
  padding: 20px 36px;
  height: fit-content;
  transition: background-color 0.6s ease-out, color 0.6s ease-out;
  line-height: 1;
  margin: 0 auto;
  margin-top: 30px;
}

.register-button.register-button-disabled {
  cursor: not-allowed;
  background-color: var(--color-gray);
}

@media (--desktop-narrow) {
  .hero-content-secondary {
    display: flex;
    flex-direction: column;
  }

  .register-button {
    width: fit-content;
    margin-top: 30px;
  }

  .cloud-icon-wrapper {
    display: none;
  }
}

@media (--mobile-wide) {
  .hero-content > * {
    transform: translateY(-10vh);
  }

  .hero-content > .icon-wrapper {
    width: 80vw;
  }

  .register-button {
    font-size: 22px;
    padding: 18px 36px;
  }
}

@media (--mobile-narrow) {
  .hero-content > h1 {
    margin-top: 30px;
    font-size: calc(3vw + 24px);
    text-align: center;
    padding: 0 30px;
    line-height: 1;
  }

  .hero-content-secondary {
    margin-top: 30px;
    padding: 0 30px;
  }

  .hero-content h2 {
    font-size: 16px;
  }

  .register-button {
    font-size: 16px;
    padding: 14px 28px;
    margin-left: auto;
    margin-right: auto;
  }
}
</style>
