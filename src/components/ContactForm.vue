<script setup>
import { ref } from 'vue';
import { CgSpinner } from "vue-icons-plus/cg";

const form = ref({
  name: "",
  email: '',
  number:'',
  subject: '',
  message: '',
})

const loading = ref(false)
const status = ref("")
const toast = ref("")

async function submitForm() {
  loading.value = true
  status.value = ""
  const body = new FormData()
  body.append("name", form.value.name)
  body.append("email", form.value.email)
  body.append("number", form.value.number)
  body.append("subject", form.value.subject)
  body.append("message", form.value.message)
  const result = await fetch("https://script.google.com/macros/s/AKfycbxRMNLC3jcIw5FGXDtKhITTd78iLEgABFxm7CtihPdqJEDuyhIs_Dkc--8QAfRxsq5PzQ/exec", {
    method: "POST",
    body
  })
  const data = await result.json()

  if (data.status==='success') {
    toast.value = 'Message sent!'
    status.value = "success"
    form.value.name = ''
    form.value.email = ''
    form.value.number = ''
    form.value.subject = ''
    form.value.message = ''
  } else {
    toast.value = "An error occured!"
    status.value = "error"
  }

  loading.value = false
  setTimeout(() => {
    toast.value = ""
  }, 5000);
}

</script>

<template>
  <section id="contact">
        <h2 class="heading">Contact</h2>
        <p>Have a Question? Check out the FAQ first!</p>

        <form method="post" name="contact-form" id="form-data">
            <div id="input-group" >
              <div>
                <input type="text" v-model="form.name" :disabled="loading" placeholder="Full Name" name="name">
                <input type="email" v-model="form.email" :disabled="loading" placeholder="Email" name="email">
                <input type="number" v-model="form.number" :disabled="loading" placeholder="Phone Number" name="number">
                <input type="text" v-model="form.subject" :disabled="loading" placeholder="Subject" name="subject">
              </div>
              <div>
                <textarea name="message" v-model="form.message" cols="30" rows="9" placeholder="Your Message"></textarea>
              </div>
            </div>
            <div id="submission">
                <button id="submit-btn" type="submit" :disabled="loading" @click="submitForm">Send Message</button>
            </div>

          </form>
        </section>
        <teleport to="body"><div v-if="toast || loading" id="formToast" :class="{'error': status==='error', 'loading': loading}">
          <button v-if="!loading" @click="toast=''">X</button>
          <p v-if="!loading">{{ toast }}</p>
          <p v-if="loading">
            <CgSpinner />
          </p>
        </div></teleport>
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

#input-group input:disabled,
#input-group textarea:disabled {
  cursor: progress;
}

#submission {

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
}
#formToast {
  position: fixed;
  bottom: 20px;
  right: 20px;
  padding: var(--sm-gap) var(--md-gap);
  background-color: var(--content-bg);
  border: var(--border);
  border-radius:10px;
  display: flex;
  flex-direction: column;
  gap: var(--md-gap);
  color: var(--primary);
  backdrop-filter: blur(10px);

  button {
    aspect-ratio: 1/1;
    padding: 5px;
    border: var(--border);
    background-color: transparent;
    border-radius: 50%;
    box-shadow: none;
    align-self: flex-end;
    color: var(--primary);
    cursor: pointer;
    transition: var(--transition);
  }
  button:hover {
    transform: scale(1.1);
  }
}
#formToast.error {
  border-color: red;

  p{
    color: white;
  }
}
#formToast.loading {
  padding: var(--lg-gap) var(--xl-gap);
  bottom: 50%;
  right: 50%;
  transform: translate(50%, 50%);

  p{
    width: max-content;
    aspect-ratio: 1/1;
    border-radius: 50%;
    transform-origin: center center;
    animation: loading 1s linear infinite ;
  }
}

@keyframes loading {
  0% {
    rotate: 0deg;
  }
  100% {
    rotate: 360deg;
  }
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
