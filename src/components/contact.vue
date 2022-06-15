<template>
  <div>
    <div class="contact">
      <h2 class="section-header sticky-top">Contact</h2>
      <div class="row">
        <div
          v-if="loader"
          class="
            col-11
            mx-auto
            d-flex
            justify-content-center
            align-items-center
            position-absolute
            w-100
            loader
          "
          style=""
        >
          <div class="sk-chase">
            <div class="sk-chase-dot"></div>
            <div class="sk-chase-dot"></div>
            <div class="sk-chase-dot"></div>
            <div class="sk-chase-dot"></div>
            <div class="sk-chase-dot"></div>
            <div class="sk-chase-dot"></div>
          </div>
        </div>
        <div class="col-11 mx-auto mt-4 contact-card">
          <div class="h4 text-white text-center mb-4 d-md-none">
            Send me an email
          </div>

          <div
            class="alert alert-success display_alert"
            role="alert"
            style="display: none"
          >
            <small>Email sent. I'll get back to you shortly.</small>
          </div>

          <form
            id="contact_form"
            method="POST"
            v-on:submit.prevent="handleFormSubmit"
          >
            <input type="hidden" name="_captcha" value="false" />
            <input
              type="hidden"
              name="_subject"
              value="New profile contact submission!"
            />

            <!-- <input type="hidden" name="_next" value="http://alaboexcel.me" /> -->

            <div class="form-group">
              <input
                type="text"
                class="form-control"
                name="full_name"
                placeholder="Full name"
                required
                v-model="name"
              />
            </div>
            <div class="form-group mt-5">
              <input
                type="email"
                class="form-control"
                name="user_email"
                placeholder="Email address"
                required
                v-model="email"
              />
            </div>
            <div class="form-group mt-5">
              <input
                type="tel"
                class="form-control"
                name="phone"
                placeholder="Phone"
                required
                v-model="phone"
              />
            </div>
            <div class="form-group mt-5">
              <textarea
                class="form-control"
                rows="4"
                name="message"
                placeholder="Message"
                required
                v-model="message"
              ></textarea>
            </div>
            <button
              type="submit"
              class="btn btn-default btn_send w-100 mt-2 text-white"
            >
              Send
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import emailjs from "emailjs-com";

export default {
  data() {
    return {
      active: false,
      loader: false,
      name: "",
      message: "",
      phone: "",
      email: "",
    };
  },
  methods: {
    handleFormSubmit: function (e) {
      this.loader = true;
      e.preventDefault();
      fetch("https://formsubmit.co/ajax/alaboexcel@gmail.com", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          Accept: "application/json",
        },
        body: JSON.stringify({
          name: this.name,
          message: this.message,
          phone: this.phone,
          email: this.email,
        }),
      })
        .then((response) => response.json())
        .then((data) => {
          console.log(data);
          if (data.success === true) {
            this.loader = false;
            this.name = "";
            this.email = "";
            this.phone = "";
            this.message = "";
            document.querySelector(".display_alert").style.display = "block";
            this.loader = false;
            setTimeout(() => {
              document.querySelector(".display_alert").style.display = "none";
            }, 2500);
          }
        })
        .catch((error) => {
          console.log(error);
          alert("An error occured, Please try again", error.text);
          this.loader = false;
          this.name = "";
          this.email = "";
          this.phone = "";
          this.message = "";
        });
    },
  },
};
</script>

<style>
.contact {
  margin-top: 100px;
}
.contact a {
  text-decoration: none;
}
.contact-card {
  padding: 40px;
  --bg-opacity: 1;
  background-color: #0c1b33;
  transition: all 0.3s ease;
  margin-bottom: 10px;
  margin: 5px;
  font-size: 18px;
}

.form-control {
  background-color: #0c1b33;
  border-left: none;
  border-right: none;
  border-top: none;
  border-radius: 0px !important;
  font-size: 16px;
  box-shadow: none;
}

/*  */
.loader {
  margin-top: 23px;
  height: 510px;
  z-index: 10;
  background-color: #0c1b33;
  opacity: 0.5;
  left: 25px;
}
.sk-chase {
  width: 40px;
  height: 40px;
  position: relative;
  animation: sk-chase 2.5s infinite linear both;
}

.sk-chase-dot {
  width: 100%;
  height: 100%;
  position: absolute;
  left: 0;
  top: 0;
  animation: sk-chase-dot 2s infinite ease-in-out both;
}

.sk-chase-dot:before {
  content: "";
  display: block;
  width: 25%;
  height: 25%;
  background-color: #fff;
  border-radius: 100%;
  animation: sk-chase-dot-before 2s infinite ease-in-out both;
}

.sk-chase-dot:nth-child(1) {
  animation-delay: -1.1s;
}
.sk-chase-dot:nth-child(2) {
  animation-delay: -1s;
}
.sk-chase-dot:nth-child(3) {
  animation-delay: -0.9s;
}
.sk-chase-dot:nth-child(4) {
  animation-delay: -0.8s;
}
.sk-chase-dot:nth-child(5) {
  animation-delay: -0.7s;
}
.sk-chase-dot:nth-child(6) {
  animation-delay: -0.6s;
}
.sk-chase-dot:nth-child(1):before {
  animation-delay: -1.1s;
}
.sk-chase-dot:nth-child(2):before {
  animation-delay: -1s;
}
.sk-chase-dot:nth-child(3):before {
  animation-delay: -0.9s;
}
.sk-chase-dot:nth-child(4):before {
  animation-delay: -0.8s;
}
.sk-chase-dot:nth-child(5):before {
  animation-delay: -0.7s;
}
.sk-chase-dot:nth-child(6):before {
  animation-delay: -0.6s;
}

@keyframes sk-chase {
  100% {
    transform: rotate(360deg);
  }
}

@keyframes sk-chase-dot {
  80%,
  100% {
    transform: rotate(360deg);
  }
}

@keyframes sk-chase-dot-before {
  50% {
    transform: scale(0.4);
  }
  100%,
  0% {
    transform: scale(1);
  }
}
@media (max-width: 1199.98px) {
  .loader {
    left: 22px;
  }
}
@media (max-width: 991.98px) {
  .loader {
    left: 29px;
  }
  .contact {
    margin-bottom: 20px;
  }
}
@media (max-width: 767.98px) {
  .contact {
    margin-top: 20px;
    margin-bottom: 10px;
  }
  .loader {
    left: 15px;
  }
}
</style>