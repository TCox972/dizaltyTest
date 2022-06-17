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
        <input type="email" placeholder="Adresse mail" />
        <button type="submit">S'INSCRIRE</button>
      </div>
    </div>
    <div>
      <ul class="social">
        <li>
          <a href="#"
            ><font-awesome-icon class="icon" icon="fa-brands fa-facebook-f"
          /></a>
        </li>
        <li>
          <a href="#"
            ><font-awesome-icon class="icon" icon="fa-brands fa-twitter"
          /></a>
        </li>
        <li>
          <a href="#"
            ><font-awesome-icon class="icon" icon="fa-brands fa-instagram"
          /></a>
        </li>
        <li>
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
  font-weight: bold;
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

.footer {
    margin-top: 48px;
  font-size: 13px;
}
</style>