<template>
  <section id="contact">
        <h2 class="heading">Contact</h2>

        <form method="post" name="contact-form" action="https://script.google.com/macros/s/AKfycbwhItEgDoIRtwYbCMVxTLtWGsTeT1OJVHdXgvYJV9bJgDh-voQl_00tHNz2gPkDOphdlg/exec" id="form-data">
            <div class="input-group">
                <div class="input-box">
                    <input type="text" placeholder="Full Name" name="name">
                    <input type="email" placeholder="Email" name="email">
                </div>
                <div class="input-box">
                    <input type="number" placeholder="Phone Number" name="number">
                    <input type="text" placeholder="Subject" name="subject">
                </div>
            </div>

            <div class="input-group2">
                <textarea name="message"  cols="30" rows="9" placeholder="Your Message"></textarea>
                <input id="submit-btn" type="submit" value="Send Message" class="btn">
            </div>

        </form>
      </section>
    </template>

<style scoped>
#contact {
  background-color: var(--bg);
  h2 {
    padding-bottom: 20px;
  }
}
#contact form{
  display: flex;
  align-items: center;
  justify-content: center;
  gap: var(--xl-gap);
  margin: 0 auto;
  text-align: center;
}
#contact form .input-box{
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
#contact form .input-box input,
#contact form textarea{
  width: 100%;
  background: var(--bg);
  border: 2px solid var(--primary);
  font-size: var(--fs-sm);
  padding: var(--md-gap);
  color: var(--txt-color);
  margin: var(--md-gap) 0;
  border-radius: 15px;
  resize: none;
}
.btn {
  margin-top: var(--md-gap);
  display: inline-block;
  padding: var(--md-gap) var(--lg-gap);
  background: var(--primary);
  box-shadow: var(--primary-shadow);
  border-radius: 20px;
  font-size: var(--fs-sm);
  color: black;
  border: 2px solid transparent;
  font-weight: 600;
  transition: 0.3s ease-in-out;
  cursor: pointer;
}
.btn:hover {
  transform: scale(1.05);
  box-shadow: var(--primary-shadow2);
}

</style>
