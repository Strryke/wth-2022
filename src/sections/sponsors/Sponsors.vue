<template>
  <section id="thankees" title="Sponsors">
    <div class="thankees-body">
      <SectionHeader>Sponsors</SectionHeader>
      <ul class="thankees-content">
        <!-- <Para style="text-align: center; margin-top: 50px;">Sponsors will be announced soon!</Para> -->
        <li class="tier" v-for="tier in tiers" :key="tier.name">
          <h3>{{ tier.name }}</h3>
          <ul class="tier-sponsors">
            <li v-for="sponsor in tier.sponsors" :key="sponsor.name">
              <a v-if="sponsor.url" :href="sponsor.url" target="_blank" rel="noopener noreferrer">
                <img
                  :class="tier.name === 'Platinum' ? 'img-platinum' : tier.name === 'Gold' ? 'img-gold' : 'img-others'"
                  style="display: var(--displayed-during-light)"
                  :src="require(`../../../public/images/${sponsor.photoNormal}.png`)"
                  :alt="`${sponsor.name} company logo`"
                />
                <img
                  :class="tier.name === 'Platinum' ? 'img-platinum' : tier.name === 'Gold' ? 'img-gold' : 'img-others'"
                  style="display: var(--displayed-during-dark)"
                  :src="require(`../../../public/images/${sponsor.photoWhite}.png`)"
                  :alt="`${sponsor.name} company logo`"
                />
              </a>
              <div v-else>
                <img
                  :class="tier.name === 'Platinum' ? 'img-platinum' : tier.name === 'Gold' ? 'img-gold' : 'img-others'"
                  style="display: var(--displayed-during-light)"
                  :src="require(`../../../public/images/${sponsor.photoWhite}.png`)"
                  :alt="`${sponsor.name} company logo`"
                />
                <img
                  :class="tier.name === 'Platinum' ? 'img-platinum' : tier.name === 'Gold' ? 'img-gold' : 'img-others'"
                  style="display: var(--displayed-during-dark)"
                  :src="require(`../../../public/images/${sponsor.photoWhite}.png`)"
                  :alt="`${sponsor.name} company logo`"
                />
              </div>
            </li>
          </ul>
        </li>
      </ul>
    </div>
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 215.4" style="transform: translateY(-7px)">
      <path
        class="slope"
        d="M0 160h60c60 0 180 0 300 16s240 48 360 37c120-10 240-64 360-85s240-11 300-5l60 5V0H0z"
      ></path>
    </svg>
  </section>
</template>

<script>
import SectionHeader from '@/components/SectionHeader.vue';
import Para from '@/components/Para';

export default {
  name: 'thankees',
  components: {
    SectionHeader,
  },
  data() {
    return {
      tiers: [
        {
          name: 'Platinum',
          sponsors: [
            {
              name: 'Indeed',
              url: 'https://www.indeed.com.sg/',
              photoNormal: 'indeed',
              photoWhite: 'indeed-white',
            },
          ],
        },
        {
          name: 'Gold',
          sponsors: [
            {
              name: 'GovTech',
              url: 'https://www.tech.gov.sg/',
              photoNormal: 'govtech',
              photoWhite: 'govtech-white',
            },
            {
              name: 'AWS',
              url: 'https://aws.amazon.com/',
              photoNormal: 'aws',
              photoWhite: 'aws-white',
            },
          ],
        },
        {
          name: 'Bronze',
          sponsors: [
            {
              name: 'Accenture',
              url: 'https://www.accenture.com/sg-en',
              photoNormal: 'accenture',
              photoWhite: 'accenture-white',
            },
            {
              name: 'IMDA',
              url: 'https://www.imda.gov.sg/',
              photoNormal: 'imda',
              photoWhite: 'imda-white',
            },
            {
              name: 'NCS',
              url: 'https://www.ncs.co/en-sg/',
              photoNormal: 'ncs',
              photoWhite: 'ncs-white',
            },
          ],
        },

        // {
        //   name: "Swag Sponsors",
        //   sponsors: [
        //     {
        //       name: "Google",
        //       url: "https://careers.google.com/locations/sing/",
        //       photoNormal: "google",
        //       photoWhite: "google-white"
        //     }
        //   ]
        // },
        // {
        //   name: "Equipment Sponsors",
        //   sponsors: [
        //     {
        //       name: "Keysight",
        //       url: "https://www.keysight.com/sg/en/home.html",
        //       photoNormal: "keysight",
        //       photoWhite: "keysight-white"
        //     }
        //   ]
        // }
      ],
    };
  },
};
</script>

<style scoped>
.thankees-body {
  background-color: var(--slope-body-color);
  width: 100%;
  padding: 100px 0;
  transform: translateY(-6px);
  transition: background-color 0.6s ease-out;
}

.thankees-content {
  margin: 0 150px;
  display: flex;
  flex-direction: column;
}

.tier {
  display: flex;
  flex-direction: column;
  text-align: center;
  margin-top: 50px;
}

.tier + .tier {
  margin-top: 150px;
}

.tier h3 {
  font-size: 20px;
  font-weight: 400;
  font-family: var(--font-secondary), sans-serif;
  color: var(--color-regular-text);
}

.tier ul {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  align-items: center;
  margin-top: 30px;
}

.tier li + li {
  margin-left: 30px;
}

.tier img.img-platinum {
  width: 350px;
}

.tier img.img-gold {
  width: 300px;
}

.tier img.img-others {
  width: 150px;
}

@media (--desktop-narrow) {
  .thankees-content {
    margin: 0 100px;
  }
}

@media (--mobile-wide) {
  .tier ul {
    flex-direction: column;
  }

  .tier li + li {
    margin-left: 0;
    margin-top: 100px;
  }
}

@media (--mobile-narrow) {
  .thankees-content {
    margin: 0 30px;
  }

  .tier + .tier {
    margin-top: 100px;
  }

  .tier li + li {
    margin-top: 50px;
  }

  .tier img.img-platinum {
    width: 250px;
  }

  .tier img.img-gold {
    width: 200px;
  }

  .tier img.img-others {
    width: 125px;
  }
}
</style>
