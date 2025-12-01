<script setup>
import { ref } from 'vue';

const formName = ref("")
const formEmail = ref("")
const formNumber = ref("")
const formSubject = ref("")
const formMessage = ref("")

const loading = ref(false)
const status = ref(null)
const statusMessage = ref("")

const closeToast = () => {
  statusMessage.value = ''
}

const submitForm = async () => {
  status.value = null
  statusMessage.value = ""
  loading.value = true

  try {
    const result = await fetch("https://script.google.com/macros/s/AKfycbzGW80D4fWrsfupni4wPB3E4UkvlzTwPFe4T3BN-Ev8N_1t1vq2oH-x4GmN-EqnOmDn0Q/exec", {
      method: "POST",
      body: JSON.stringify({
        name: formName.value,
        email: formEmail.value,
        number: formNumber.value,
        subject: formSubject.value,
        message: formMessage.value
      }),
      headers: { "Content-Type": "application/json"}
    });
    const data = await result.json()
    if (data.success) {
      status.value = "success"
      statusMessage.value = data.message
    } else {
      status.value = "error"
      statusMessage.value = data.message || "An unknown error occured"
    }
  } catch (error) {
    status.value = "error"
    statusMessage.value = error.message
  }
  loading.value = false
}

</script>

<template>
  <section id="contact">
        <h2 class="heading">Contact</h2>
        <p>Have a Question? Check out the FAQ first!</p>

        <form method="post" name="contact-form" id="form-data">
            <div id="input-group" :disabled="loading">
              <div>
                <input type="text" v-model="formName" placeholder="Full Name" name="name">
                <input type="email" v-model="formEmail" placeholder="Email" name="email">
                <input type="number" v-model="formNumber" placeholder="Phone Number" name="number">
                <input type="text" v-model="formSubject" placeholder="Subject" name="subject">
              </div>
              <div>
                <textarea name="message" v-model="formMessage" cols="30" rows="9" placeholder="Your Message"></textarea>
              </div>
            </div>
            <div id="submission">
                <button id="submit-btn" type="submit" :disabled="loading" @submit.prevent="submitForm">Send Message</button>
            </div>
            <teleport v-if="statusMessage" to="body"><div id="formToast"><button @click="closeToast">X</button><p>{{ statusMessage }}</p></div></teleport>

        </form>
      </section>
    </template>

<style scoped>
#contact {
  background-color: var(--bg);
  min-height: auto;
  h2 {
    padding-bottom: 20px;
  }
  p {
    text-align: left;
    padding-bottom: var(--md-gap);
  }
}
#contact form{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: var(--md-gap);
  margin: 0 auto;
  text-align: center;
}
#contact form #input-group {
  width: 100%;
  display: flex;
  flex-direction: row;
  gap: var(--md-gap);
  justify-content: space-evenly;
  flex-wrap: wrap;
}

#input-group div{
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  width: 45%;
}

#input-group input,
#input-group textarea{
  background: var(--bg);
  border: 2px solid var(--primary);
  padding: var(--sm-gap);
  font-size: var(--fs-sm);
  color: var(--txt-color);
  margin: var(--sm-gap) 0;
  border-radius: 15px;
  resize: none;
}
button {
  margin-top: var(--md-gap);
  font-size: var(--fs-sm);
  display: inline-block;
  padding: var(--sm-gap) var(--md-gap);
  background: var(--primary);
  box-shadow: var(--primary-shadow);
  border-radius: 20px;
  color: black;
  border: 2px solid transparent;
  font-weight: 600;
  transition: 0.3s ease-in-out;
  cursor: pointer;
}
button:hover {
  transform: scale(1.05);
  box-shadow: var(--primary-shadow2);
}

@media screen and (max-width: 600px) {
  #contact form #input-group{
    flex-direction: column;
    align-items: center;
    gap: 0px;
  }
  #input-group div {
    width: 80%;
  }
}

@media screen and (max-width:400px) {
  #input-group div {
    width: 90%;
  }
}

</style>
