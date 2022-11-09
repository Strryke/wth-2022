<template>
  <section id="contact" title="Contact Us">
    <div class="contact-body">
      <SectionHeader>Contact Us</SectionHeader>
      <form class="contact-content" id="contact-form" name="contact-form" ref="form" @submit.prevent="sendEmail">
        <FormInput
          type="text"
          label="*Name"
          name="name"
          placeholder="Your cool name :)"
          :model="contacteeName"
          :onBlur="validateFilled"
        />
        <FormInput
          type="text"
          label="*Email Address"
          name="email"
          placeholder="No spam, promise!"
          :model="contacteeEmail"
          :onBlur="
            (s) => {
              if (!validateFilled(s)) {
                validateEmail(s);
              }
            }
          "
        />
        <Textbox
          label="*What would you like to talk to us about?"
          name="message"
          :model="contacteeMessage"
          :onBlur="validateFilled"
          placeholder="Anything is fine! Your questions, feedback, suggestions, etc."
        />
        <button type="submit" class="form-button">Submit</button>
      </form>
      <div class="submission-container">
        <!-- <FormButton
          id="contact-submission-confirmation-modal-button"
          linkAction="non-router"
          :onClick="{
            func: openModal,
            args: ['contact-submission-confirmation-modal', 'contact-submission-confirmation-modal-button'],
          }"
          >Submit</FormButton
        > -->
        <FormError
          class="submission-error"
          :style="submissionMsg.type === 'positive' ? 'color: var(--color-accent);' : null"
          >{{ submissionMsg.msg }}</FormError
        >
        <button type="submit" value="Send" />
      </div>
    </div>
    <svg viewBox="0 0 1440 320" xmlns="http://www.w3.org/2000/svg" style="transform: translateY(-7px);">
      <path
        class="slope"
        d="m0 128 48 16c48 16 144 48 240 75 96 26 192 48 288 48s192-22 288-22 192 22 288 38 192 26 240 32l48 5v-320h-1440z"
      ></path>
    </svg>
    <ConfirmationModal
      id="contact-submission-confirmation-modal"
      :positiveFunc="
        () => {
          if (!validateAll()) {
            submitForm('contact-form');
          }
        }
      "
      >Are you sure you want to submit the form?</ConfirmationModal
    >
  </section>
</template>

<script>
import SectionHeader from '@/components/SectionHeader.vue';
import FormInput from '@/components/FormInput.vue';
import Textbox from '@/components/Textbox.vue';
import FormButton from '@/components/FormButton.vue';
import FormError from '@/components/FormError.vue';
import ConfirmationModal from '@/components/ConfirmationModal.vue';

import validateFilledMixin from '@/mixins/validateFilledMixin';
import validateEmailMixin from '@/mixins/validateEmailMixin';
import openModalMixin from '@/mixins/openModalMixin';
import emailjs from '@emailjs/browser';

export default {
  name: 'contact',
  components: {
    SectionHeader,
    FormInput,
    Textbox,
    // FormButton,
    FormError,
    ConfirmationModal,
  },
  data() {
    return {
      contacteeName: { value: '', error: '' },
      contacteeEmail: { value: '', error: '', success: false },
      contacteeMessage: { value: '', error: '' },
      submissionMsg: { type: 'negative', msg: '' },
    };
  },
  mixins: [validateFilledMixin, validateEmailMixin, openModalMixin],
  methods: {
    validateAll() {
      let testNum = 0;
      let validationConclusion = '';

      testNum += this.validateFilled(this.contacteeName);
      testNum += this.validateFilled(this.contacteeMessage);
      if (!this.validateFilled(this.contacteeEmail)) {
        testNum += this.validateEmail(this.contacteeEmail);
      } else {
        testNum++;
      }

      if (testNum) {
        validationConclusion = 'There are some incomplete fields or invalid responses.';
      }

      this.submissionMsg = { type: 'negative', msg: validationConclusion };
      return validationConclusion;
    },
    // submitForm(id) {
    //   let form = document.getElementById(id);
    //   fetch(form.action, {
    //     method: 'POST',
    //     body: new URLSearchParams(new FormData(form)),
    //   })
    //     .then(() => {
    //       this.contacteeName = { value: '', error: '' };
    //       this.contacteeEmail = { value: '', error: '', success: false };
    //       this.contacteeMessage = { value: '', error: '' };
    //       this.submissionMsg = {
    //         type: 'positive',
    //         msg: 'Your message has been received and we will get back to you shortly. Cheers!',
    //       };
    //     })
    //     .catch(() => {
    //       this.submissionMsg = {
    //         type: 'negative',
    //         msg: "Sorry, but there seems to be a problem and we didn't receive your message. Please try resubmitting!",
    //       };
    //     });
    // },
    sendEmail() {
      if (!this.validateAll()) {
        emailjs.sendForm('service_q9p4p8c', 'sutdwth', this.$refs.form, 'EfE0WUzQ5bXAeSaDj').then(
          (result) => {
            alert('Your message has been received and we will get back to you shortly. Cheers!');
            this.$refs.form.reset();
          },
          (error) => {
            alert('Something went wrong, please try again or email us directly at sutdwth@gmail.com');
          },
        );
      }
    },
  },
};
</script>

<style scoped>
.contact-body {
  background-color: var(--slope-body-color);
  width: 100%;
  padding: 60px 0;
  transform: translateY(-6px);
  transition: background-color 0.6s ease-out;
}

h3 {
  font-family: var(--font-secondary), sans-serif;
  font-size: calc(24px + 2vw);
  font-weight: 700;
  padding-left: 150px;
  color: var(--color-section-title-text);
  margin-bottom: 50px;
}

.contact-content {
  margin: 0 150px;
}

.submission-container {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  margin: 100px 150px 0 150px;
}

@media (--desktop-narrow) {
  h3 {
    padding-left: 100px;
  }

  .contact-content {
    margin: 0 100px;
  }

  .submission-container {
    margin: 100px 100px 0 100px;
  }
}

@media (--mobile-narrow) {
  h3 {
    padding-left: 30px;
  }

  .contact-content {
    margin: 0 30px;
  }

  .submission-container {
    margin: 100px 30px 0 30px;
  }
}

.form-button {
  cursor: pointer;
  font-family: var(--font-primary), sans-serif;
  font-size: 24px;
  font-weight: 700;
  color: var(--slope-body-color);
  padding: 4px 20px;
  background-color: var(--color-regular-text);
  border: none;
}

.form-button:disabled {
  opacity: 0.4;
  cursor: not-allowed;
}

@media (--mobile-narrow) {
  .form-button {
    font-size: 20px;
  }
}
</style>
