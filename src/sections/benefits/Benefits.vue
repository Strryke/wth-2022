<template>
  <section id="benefits" title="benefits">
    <div class="benefits-body">
      <SectionHeader style="text-align: center; padding-left: 0">Participant Benefits</SectionHeader>
      <div class="benefits-content">
        <div class="type" v-for="benefit in benefit" :key="benefit.name">
          <SubHeader style="align-self: center" class="benefits-subheader">{{ benefit.name }}</SubHeader>
          <Para style="margin-top: 30px">{{ benefit.description }}</Para>
          <ul>
            <ul class="benefit" v-for="things in benefit.things" :key="things">
              <!-- <div style="display: flex; margin: 0 auto;"> -->
              <li class="things">
                {{ things }}
              </li>
              <!-- </div> -->
            </ul>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import SectionHeader from '@/components/SectionHeader.vue';
import SubHeader from '@/components/SubHeader.vue';
import Para from '@/components/Para.vue';

export default {
  name: 'benefits',
  components: {
    SectionHeader,
    SubHeader,
    Para,
  },
  data() {
    return {
      benefit: [
        {
          name: 'Makerspace',
          description: '',
          things: ['3D printer', 'Laser Cutter', 'Acrylic Benders', 'Bandsaw', 'Drill Press', 'Electronics Lab'],
        },
        {
          name: 'Hackpack',
          description: '',
          things: [
            'Arduino Uno',
            'RFID module',
            'Character LCDs',
            '7-Segment Displays',
            'Infrared Remotes',
            'Carrying Case',
            '...and more!',
          ],
        },
      ],
    };
  },
};
</script>

<style scoped>
.benefits-body {
  background-color: var(--slope-body-color);
  width: 100%;
  padding: 50px 0px;
  transform: translateY(-1px);
  transition: background-color 0.6s ease-out;
}

.benefits-subheader {
  margin-bottom: 20px;
  text-align: center;
}

.benefits-content {
  width: 100%;
  margin: 0 auto;
  padding: 0 150px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}

.category {
  display: flex;
  flex-direction: column;
}

.type {
  width: 100%;
  margin: 0 auto;
  padding-top: 70px;
  display: flex;
  flex-direction: column;
}

.things {
  font-size: 24px;
  font-family: var(--font-primary), sans-serif;
  line-height: 1.6;
  color: var(--color-regular-text);
  /* list-style-type: circle; */
  /* list-style-position: inside; */
  text-align: center;
}

.category h3 {
  font-size: 32px;
  font-family: var(--font-secondary), sans-serif;
  color: var(--color-regular-text);
  align-self: center;
  border-bottom: 10px solid var(--color-accent);
  line-height: 0.4;
  text-decoration: none;
}

@media (max-width: 668px) {
  .benefits-subheader {
    font-size: 24px;
  }

  .benefits-content {
    grid-template-columns: repeat(1, 1fr);
  }
}

@media (max-width: 410px) {
  .benefits-subheader {
    font-size: 17.5px;
  }
}
</style>
