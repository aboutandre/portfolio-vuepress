<template>
  <div class="contact-content">
    <h2>{{ contactTitle }}</h2>

    <form
      name="contact"
      class="contact-form"
      method="POST"
      netlify-honeypot="bot-field"
      data-netlify="true"
    >
      <p class="hidden">
        <label>
          Don’t fill this out if you're human:
          <input name="bot-field">
        </label>
      </p>
      <label>
        Email:
        <input type="email" name="email">
      </label>
      <label>
        Message:
        <textarea name="message" placeholder="eg.:&quot;When are you available?&quot;"></textarea>
      </label>
      <div data-netlify-recaptcha="true" class="captcha"></div>
      <button type="submit" class="button">Send</button>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    contactTitle: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
.contact-content {
  width: 100%;
}

.contact-form > * + * {
  margin-top: 1.5em;
}

.button {
  background-color: #333;
  border-radius: 5px;
  /* border: 1px solid #333; */
  color: #fcfcfc;
  font-family: inherit;
  font-size: inherit;
  min-height: 3em;
}

@media screen and (min-width: 400px) {
  .contact-content {
    max-width: 400px;
    width: 75vw;
  }
}

form {
  align-content: center;
  display: flex;
  flex-direction: column;
  width: 100%;
}
.hidden {
  display: none;
}
input,
textarea {
  border: 1px solid gainsboro;
  border-radius: 5px;
  font-family: inherit;
  font-size: inherit;
  margin-top: 0.5em;
  max-width: 400px;
  min-height: 2em;
  padding: 0.5em;
}
textarea {
  min-height: 4em;
}
label {
  display: flex;
  flex-direction: column;
  flex-basis: 100%;
}
.captcha {
  margin: 0 !important;
}
</style>
