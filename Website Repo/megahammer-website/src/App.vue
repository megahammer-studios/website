<template>
  <div class="main">
    <PageHeader/>
    <div class="content">
      <div class="videosection">

        <div class="videosection-content">

          <div class="video-player" :class="{hidden: playerhidden}" ref="player">

            <vue-plyr ref="plyr">
              <div class="plyr__video-embed">
                <iframe
                    src="https://youtu.be/MjkMnHJAs4Y"
                    allowfullscreen
                    allowtransparency
                    allow="autoplay"
                ></iframe>
              </div>
            </vue-plyr>

          </div>
        </div>
      </div>

      <div class="contentsection">
        <div class="about">
          <div class="title">ABOUT</div>

          <div class="about-row">
            <div>
              <img src="./assets/donovan.jpg" class="about-image">
            </div>
            <div class="text">
              Donovan Jonk is a multi-instrumentalist, composer, and sound designer. With a Bachelor of Music in jazz studies and music technology from Minnesota State University Moorhead, and a varied career in the music industry as a teacher, performer, freelance composer, and indie record label associate, Donovan comes with the experience and instincts to help your project find its unique sonic identity.
            </div>
          </div>


        </div>
      </div>

      <div class="bgsection">
        <div class="title">PROJECTS</div>

        <div class="project-list">
          <div class="project" v-for="project in projects" :key="project.link">
            <div class="project-inner">
              <a :href="project.link">
                <img :src="project.image" class="project-image"/>
              </a>
              <div class="project-inner-overlay">
                {{project.text}}
              </div>
            </div>
            <div class="project-title">{{project.name}}</div>
          </div>
        </div>

        <div class="title">OTHER FUN STUFF</div>

        <div class="project-list">
          <div class="project" v-for="project in other_fun_stuff" :key="project.link">
            <div class="project-inner">
              <a :href="project.link">
                <img :src="project.image" class="project-image"/>
              </a>
              <div class="project-inner-overlay">
                {{project.text}}
              </div>
            </div>
            <div class="project-title">{{project.name}}</div>
          </div>
        </div>

      </div>

      <div class="contentsection">
        <div class="title">CONTACT</div>

        <form class="contact-form" method="POST" data-netlify="true"
              data-netlify-honeypot="bot-field" name="contact-form">
          <input type="hidden" name="form-name" value="contact-form" />
          <div class="input-row">
            <div class="col">
              <div class="label">Name:</div>
              <div class="input-row">
                <input v-model="name" class="input input-name" name="name"/>
              </div>
            </div>
            <div class="col">
              <div class="label">Surname:</div>
              <div class="input-row">
              <input v-model="surname" class="input input-surname" name="surname"/>
              </div>
            </div>
          </div>
          <div class="label">Email:</div>
          <input v-model="email" class="input input-email" name="email"/>
          <div class="label">Subject:</div>
          <input v-model="subject" class="input input-subject" name="subject"/>
          <div class="label">Message:</div>
          <textarea v-model="message" class="input input-message" name="message"/>

          <div class="field">
            <div data-netlify-recaptcha="true"></div>
          </div>

          <div class="button-row">
            <input type="submit" value="SUBMIT" class="submit-button">
          </div>
        </form>
      </div>

      <div class="footer">
        <div class="socials">
          <a href="https://twitter.com/Megahammeraudio">
            <img src="./assets/twitter.png"/>
          </a>
          <a href="https://www.instagram.com/megahammerstudios/">
            <img src="./assets/instagram.png"/>
          </a>
          <a href="https://www.youtube.com/channel/UCGbR_xC94Z0zsNQtgOMziqQ">
            <img src="./assets/youtube.png"/>
          </a>
        </div>

      </div>

    </div>
  </div>
</template>

<script>

import PageHeader from "@/components/PageHeader";
export default {
  name: 'App',
  components: {PageHeader},
  data() {
    return {
      name: "",
      surname: "",
      email: "",
      subject: "",
      message: "",
      projects: [
        {
          image: require("./assets/projects/kaiju_wars-game.png"),
          text: "sound design",
          link: "https://store.steampowered.com/app/1508400/Kaiju_Wars/",
          name: "Kaiju Wars"
        },
        {
          image: require("./assets/projects/constellations-game.png"),
          text: "music + sound design",
          link: "https://raindrinker.com/#/games",
          name: "Constellations"
        },
        {
          image: require("./assets/projects/chicken_journey-game.png"),
          text: "music + sound design",
          link: "https://store.steampowered.com/app/1837650/Chicken_Journey/",
          name: "Chicken Journey"
        },
        {
          image: require("./assets/projects/blood_nova-game.png"),
          text: "music",
          link: "https://store.steampowered.com/app/1810270/Blood_Nova/",
          name: "Blood Nova"
        },
        {
          image: require("./assets/projects/chiefswood_VR-game.png"),
          text: "music + sound design",
          link: "https://zenfri.com/three-sisters-vr-experience/",
          name: "Three Sisters VR"
        },
        {
          image: require("./assets/projects/ChiefswoodAR_Poster-small.png"),
          text: "sound design",
          link: "https://zenfri.com/chiefswood-park-augmented-reality-tour/",
          name: "Chiefswood Park AR"
        },
        {
          image: require("./assets/projects/YCSEAO+_game.png"),
          text: "sound design",
          link: "https://sebastianscaini.itch.io/ycseao-plus",
          name: "YCSEAO"
        },
        {
          image: require("./assets/projects/fancy_trash-game.png"),
          text: "music + sound design",
          link: "https://sebastianscaini.itch.io/fancy-trash",
          name: "Fancy Trash"
        },
        {
          image: require("./assets/projects/cheekynauts_valentine-game.png"),
          text: "music + sound design",
          link: "http://www.cheekynauts.com/cheeky_valentine/story_html5.html",
          name: "Cheekynauts"
        },
        {
          image: require("./assets/projects/annie_and_the_shadow_palace.png"),
          text: "music + sound design",
          link: "https://store.steampowered.com/app/1587220/Annie_and_the_Shadow_Palace/",
          name: "Annie and the Shadow Palace"
        },
        {
          image: require("./assets/projects/BrandinsButtons-Header.png"),
          text: "music",
          link: "https://store.steampowered.com/app/1480970/Brandins_Buttons/",
          name: "Brandin's Buttons"
        },
        {
          image: require("./assets/projects/the_flame-game.png"),
          text: "music + sound design",
          link: "https://sebastianscaini.itch.io/the-flame",
          name: "The Flame"
        }
      ],
      other_fun_stuff: [
        {
          image: require("./assets/projects/8bit_bundle-Raindrinker.png"),
          text: "music + sfx asset bundle",
          link: "https://megahammer-studios.itch.io/8-bit-music-and-sfx-megahammer-studios-vol-1",
          name: "8-bit bundle"
        },
        {
          image: require("./assets/projects/massive_corp-logo.png"),
          text: "logo sound design",
          link: "http://massivecorp.ca/",
          name: "Massive Corp Logo SFX"
        },
        {
          image: require("./assets/projects/Alchemy-video-01.00_00_43_13.Still001.png"),
          text: "multimedia music + sound design",
          link: "https://www.youtube.com/watch?v=vvOvTafi2MU&list=PL2L2NIX4GhktouJQHZFtAcNkJdYjaDSv7&index=1",
          name: "Stream collab #1"
        },
        {
          image: require("./assets/projects/spookcollab.00_02_15_11.Still001.png"),
          text: "multimedia music + sound design",
          link: "https://youtu.be/cdaQ9McZOqQ",
          name: "Stream collab #2"
        }
      ]
    }
  },
  mounted() {
    this.$refs.plyr.player.on('ended', () => this.videoEnded())
  },
  methods: {
    onClickMonke() {
      this.playerhidden = false;
    },
    videoEnded() {
      this.$refs.plyr.player.restart();
      this.$refs.plyr.player.stop();
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  margin: 0;
  height: 100vh;
  width: 100%;

  display: flex;
  flex-direction: column;
}

body {
  margin: 0;
  background-color: black;
}

.main {

  width: 100%;

  display: flex;
  flex-direction: column;

}

.logo-monke {
  max-width: 100%;
  position: absolute;

  z-index: 400;
}

.text {
  color: #AAAAAA;
  font-size: 24px;
}

.content {

  display: flex;

  flex-direction: column;

  align-items: center;
  justify-content: center;

  flex-shrink: 0;

  background-image: url("./assets/hammerpattern.png");
  background-attachment: fixed;
  background-position: center;
  background-repeat: repeat;
  background-size: 100px;

}

.videosection {

  height: 100vh;

  width: 100%;

  position: relative;
}

.videosection-content {

  padding: 32px;
  padding-top: 300px;


  position: relative;

  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.contentsection {
  width: 100%;

  background-color: #222222;

  min-height: 300px;

  color: #EEEEEE;

  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.3);
}

.bgsection {

  min-height: 300px;

  display: flex;
  flex-direction: column;
  align-items: center;
}

.footer {

  width: 100%;

  height: 150px;

  background-color: #050505;
}

.about {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.title {
  color: white;
  font-size: 32px;
  padding-top: 32px;
}

.about .text {
  text-align: left;
  max-width: 800px;
  padding-right: 64px;
}

.about-row {
  display: flex;
  align-items: center;

  padding-bottom: 64px;
}


.about-image {
  max-width: 250px;

  border-radius: 1000px;
  padding: 64px;
}

.video-player {
  width: 100%;

  max-width: 1000px;

  transition: 0.5s;

  margin-top: -40px;

  border-radius: 16px;
  overflow: hidden;

  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.3);
}

.project-list {
  display: flex;
  flex-wrap: wrap;

  align-items: center;
  justify-content: center;

  max-width: 80%;

  padding-bottom: 64px;
  padding-top: 32px;
}

.project {

  padding: 32px;
}

.project-inner {
  background-color: #111111;
  width: 300px;
  height: 170px;

  border-radius: 16px;
  overflow: hidden;

  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.3);
  position: relative;
}

.project-image {
  width: 300px;
}

.project-title {
  padding-top: 8px;
  color: white;
  font-weight: bold;
}

.project-inner-overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: transparent;
  color: transparent;

  left: 0;
  top: 0;

  display: flex;
  align-items: center;
  justify-content: center;

  pointer-events: none;

  transition: 0.2s;

  font-weight: bold;
}

.project-inner:hover .project-inner-overlay{

  background-color: #000000AA;
  color: white;
}

.contact-form {
  display: flex;
  flex-direction: column;
  padding: 20px 20% 100px 20%;
}

.input-row {
  display: flex;
  flex-direction: row;
  width: 100%;
}

.contact-form .input {
  padding: 8px;
  border-radius: 8px;
  border: none !important;
  margin: 8px;

  flex-grow: 1;
}

textarea.input {
  height: 100px;
  resize: none;
}

input {
  border: none;
  outline: none;
}

textarea {
  outline: none;
}

input:focus {
  border: none;
  outline: none;
}

.button-row {
  display: flex;
  justify-content: end;
}

.submit-button {
  padding: 12px;

  margin-top: 8px;
  margin-right: 8px;

  font-weight: bold;
  font-size: 18px;

  background-color: #111111;
  color: #CCCCCC;

  border: none;

  border-radius: 8px;

  cursor: pointer;

}

.col {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  align-items: start;
}

.label {
  font-weight: bold;
  padding-left: 8px;
  text-align: left;
}

.socials {
  padding-top: 32px;
}

.socials img {
  height: 32px;
  padding: 8px;
  opacity: 0.6;
  transition: 0.2s;
}

.socials img:hover {
  opacity: 1;
}

@media only screen and (max-width: 800px) {
  .about-row {
    flex-direction: column;
  }

  .about-image {
    padding: 32px;
  }

  .about .text {
    padding: 32px;
  }
}

@media only screen and (max-width: 600px) {

  .about .text {
    font-size: 20px;
  }

  .input-row {
    flex-direction: column;
  }

  .contact-form {
    padding: 32px;
  }
}

</style>
