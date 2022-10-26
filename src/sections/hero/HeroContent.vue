<template>
  <div class="hero-content">
    <div class="icon-wrapper">
      <WTHIcon />
    </div>
    <h1>A Brighter Future</h1>
    <div class="hero-content-secondary">
      <div>
        <h2>19th - 20th December 2022 @ SUTD</h2>
      </div>
    </div>
    <button class="cta-button" role="button">Sign Up Now!</button>

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
  },
  mixins: [openModalMixin],
};
</script>

<style scoped>
/* CSS */
.cta-button {
  align-items: center;
  background-color: var(--color-title-text);
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 0.25rem;
  box-shadow: rgba(0, 0, 0, 0.02) 0 1px 3px 0;
  box-sizing: border-box;
  color: var(--color-cta-text);
  cursor: pointer;
  display: inline-flex;
  font-family: system-ui, -apple-system, system-ui, 'Helvetica Neue', Helvetica, Arial, sans-serif;
  font-size: 24px;
  font-weight: 600;
  justify-content: center;
  line-height: 1.25;
  margin: 30px auto;
  min-height: 3rem;
  padding: calc(0.875rem - 1px) calc(1.5rem - 1px);
  position: relative;
  text-decoration: none;
  transition: all 250ms;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: baseline;
  width: fit-content;
}

.cta-button:hover,
.cta-button:focus {
  border-color: var(--color-accent);
  box-shadow: rgba(0, 0, 0, 0.1) 0 4px 12px;
}

/* .cta-button:hover {
  transform: translateY(-1px);
} */

.cta-button:active {
  background-color: #f0f0f1;
  border-color: rgba(0, 0, 0, 0.15);
  box-shadow: rgba(0, 0, 0, 0.06) 0 2px 4px;
}

.hero-content {
  position: relative;
  height: 87.5%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  background: url(../../../public/images/slide1.jpg) no-repeat bottom center;
  -webkit-background-size: contain;
  -moz-background-size: contain;
  -o-background-size: contain;
  background-size: contain;
  background-color: var(--color-background-1);
}

.hero-content > .icon-wrapper {
  width: calc(400px + 30vw);
  margin: 0 auto;
}
.cloud-icon-wrapper {
  position: absolute;
  top: 0;
  right: 0;
  transform: translateX(80%);
  width: 23vw;
  max-width: 300px;
}
.hero-content h1 {
  font-family: var(--font-secondary), sans-serif;
  font-size: calc(2vw + 14px);
  font-weight: 900;
  color: var(--color-title-text);
  margin: 0 auto;
  margin-bottom: 8px;
  transition: color 0.6s ease-out;
}
.hero-content-secondary {
  display: flex;
  margin: 0 auto;
}
.hero-content h2 {
  font-family: var(--font-primary), sans-serif;
  font-size: calc(1vw + 10px);
  font-weight: 400;
  color: var(--color-title-text);
  transition: color 0.6s ease-out;
}

.register-button {
  display: flex;
  align-items: center;
  margin-left: 20px;
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
  margin-top: 20px;
  text-align: center;
}
.register-button.register-button-disabled {
  cursor: not-allowed;
  background-color: var(--color-gray);
}
.caution-button {
  display: inline-flex;
  align-items: center;
  text-align: center;
  margin-left: 20px;
  text-decoration: none;
  font-size: 24px;
  font-family: var(--font-secondary), sans-serif;
  font-weight: 700;
  background-color: var(--color-accent);
  color: var(--color-caution-text);
  padding: 32px 40px;
  width: 265px;
  height: 0;
  transition: background-color 0.6s ease-out, color 0.6s ease-out;
  line-height: 0px;
}
@media (max-width: 1180px) {
  .caution-button {
    padding: 32px 31px;
  }
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
  .caution-button {
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
    margin-left: 8vw;
  }
  .register-button {
    font-size: 22px;
    padding: 18px 36px;
  }
  .caution-button {
    font-size: 22px;
    padding: 28px 35px;
    width: 240px;
  }
}
@media (--mobile-narrow) {
  .hero-content > svg {
  }
  .hero-content > h1 {
    margin-top: 30px;
    font-size: calc(3vw + 24px);
    margin-left: 0;
    text-align: center;
    padding: 0 30px;
    line-height: 1;
  }
  .hero-content-secondary {
    margin-top: 30px;
    /* margin-left: 0; */
    text-align: center;
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
  .caution-button {
    font-size: 16px;
    padding: 22px 30px;
    width: 185px;
    margin-left: auto;
    margin-right: auto;
  }
}
</style>
