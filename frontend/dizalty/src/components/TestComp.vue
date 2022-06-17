<template>
  <div class="home">
    <img class="logo" src="../../public/images/logo.png" alt="logo" />
    <div>
      <ul class="countdown">
        <li>
          <span class="days">{{ days }}</span>
          <p class="lbl">{{ labeldays }}</p>
        </li>
        <li>
          <span class="hours">{{ hours }}</span>
          <p class="lbl">{{ labelhours }}</p>
        </li>
        <li>
          <span class="mins">{{ mins }}</span>
          <p class="lbl">{{ labelmins }}</p>
        </li>
        <li>
          <span class="scds">{{ scds }}</span>
          <p class="lbl">{{ labelscds }}</p>
        </li>
      </ul>
    </div>
    <div class="inscription">
      <p class="notif">{{ notif }}</p>
      <div class="field">
        <transition name="slide-fade">
          <div class="emailerror" v-if="emailerror">
            <p>Veuillez fournir une adresse électronique valide</p>
          </div>
        </transition>

        <input type="email" v-model="email" placeholder="Adresse mail" />
        <button type="submit" @click="submitEmail">S'INSCRIRE</button>
      </div>
    </div>
    <div>
      <ul class="social">
        <li id="facebook">
          <a href="#"
            ><font-awesome-icon class="icon" icon="fa-brands fa-facebook-f"
          /></a>
        </li>
        <li id="twitter">
          <a href="#"
            ><font-awesome-icon class="icon" icon="fa-brands fa-twitter"
          /></a>
        </li>
        <li id="insta">
          <a href="#"
            ><font-awesome-icon class="icon" icon="fa-brands fa-instagram"
          /></a>
        </li>
        <li id="google">
          <a href="#"
            ><font-awesome-icon class="icon" icon="fa-brands fa-google"
          /></a>
        </li>
      </ul>
    </div>
    <div class="footer">
      <p>Juste histoire de faire un footer</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "TestComp",

  data: () => ({
    notif: "Dizalty arrive bientôt... Inscrivez-vous pour être informé.",
    days: "",
    labeldays: "DAYS",
    hours: "",
    labelhours: "HOURS",
    mins: "",
    labelmins: "MINUTES",
    scds: "",
    labelscds: "SECONDS",
    email: "",
    emailerror: false,
  }),

  created() {
    setInterval(() => {
      const today = new Date().getTime();
      const cdDate = new Date("09/01/2022 07:00:00").getTime();

      const diff = cdDate - today;

      var days = Math.floor(diff / (1000 * 60 * 60 * 24));
      if (days < 10) {
        days = "0" + days;
      }
      if (days <= 1) {
        this.labeldays = "DAY";
      } else {
        this.labeldays = "DAYS";
      }
      this.days = days;

      var hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      if (hours < 10) {
        hours = "0" + hours;
      }
      if (hours <= 1) {
        this.labelhours = "HOUR";
      } else {
        this.labelhours = "HOURS";
      }
      this.hours = hours;

      var mins = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
      if (mins < 10) {
        mins = "0" + mins;
      }
      if (mins <= 1) {
        this.labelmins = "MINUTE";
      } else {
        this.labelmins = "MINUTES";
      }
      this.mins = mins;
      var scds = Math.floor((diff % (1000 * 60)) / 1000);
      if (scds < 10) {
        scds = "0" + scds;
      }
      if (scds <= 1) {
        this.labelscds = "SECOND";
      } else {
        this.labelscds = "SECONDS";
      }
      this.scds = scds;
    }, 1000);
  },

  methods: {
    submitEmail() {
      const email = this.email;
      const EMAIL_REGEX =
        /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;

      if (!EMAIL_REGEX.test(email)) {
        return (this.emailerror = true);
      }

      alert(
        "Impossible de se connecter au serveur d'enregistrement. Veuillez réessayer plus tard."
      );
    },
  },
};
</script>

<style scoped>
.logo {
  width: 300px;
}

.notif {
  font-size: 18px;
  font-weight: 500;
  margin-top: 0px;
}

.countdown {
  display: block;
  padding-inline-start: 0px;
  margin: 75px 0px;
  text-align: center;
}

.countdown > li {
  display: inline-block;

  list-style: none;
  margin-right: 30px;
}

.countdown > li > span {
  line-height: 80px;
  font-size: 80px;
  font-weight: 500;
}

.countdown > li > p {
  margin: 0px;
}

.lbl {
  font-size: 16px;
}

.field {
  margin: auto;
  position: relative;
  width: 520px;
  color: white;
}

.emailerror {
  border: solid 1px rgb(153, 15, 0);
  margin: 0px 0px 12px 0px;
  background-color: rgb(223, 169, 169);
}

.emailerror > p {
  margin: 0px;
  padding: 8px;
  font-weight: 600;
  color: rgb(153, 15, 0);
}

.slide-fade-enter-active {
  transition: all .3s ease;
}

.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}

.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateY(10px);
  opacity: 0;
}

input {
  height: 50px;
  width: 350px;
  padding-left: 20px;
  padding-right: 145px;
  color: white;
  font-size: 14px;
  font-weight: 600;
  border: solid 3px white;
  background: rgba(255, 255, 255, 0.1);
}

input::placeholder {
  color: white;
  font-weight: 600;
}

button {
  position: absolute;
  bottom: 1px;
  right: 5px;
  background-color: white;
  border: none;
  height: 55px;
  width: 115px;
  padding: 0px 20px;
  font-size: 13px;
  font-weight: bold;
}

button:hover {
  background-color: yellow;
  cursor: pointer;
}

.icon {
  text-decoration: none;
}

.social {
  display: flex;
  justify-content: center;
  width: 300;
  margin-top: 42px;
  text-align: center;
  flex-direction: row;
  padding-inline-start: 0px;
}

.social > li {
  display: flex;
  justify-content: center;
  align-items: center;
  list-style: none;
  height: 45px;
  width: 45px;
  border: solid 2px white;
  border-radius: 100%;
  cursor: pointer;
  margin-right: 7px;
}

.icon {
  margin-top: 3px;
}

a {
  width: auto;
  color: white;
  font-weight: 400;
  font-size: 20px;
  text-decoration-color: white;
  text-decoration-line: none;
}

#facebook, #twitter, #insta, #google {
    transition: background-color 0.4s;
}

#facebook:hover {
  background-color: rgb(59, 89, 153);
  border-color: rgb(59, 89, 153);
}
#twitter:hover {
  background-color: rgb(85, 172, 239);
  border-color: rgb(85, 172, 230);
}
#insta:hover {
  background-color: rgb(158, 111,80);
  border-color: rgb(158,111, 80);
}
#google:hover {
  background-color: rgb(222, 75, 57);
  border-color: rgb(222, 75, 57);
}


.footer {
  margin-top: 48px;
  font-size: 13px;
  font-weight: 500;
}
</style>