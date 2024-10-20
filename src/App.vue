<template>
  <div id="app">
    <div class="background-overlay"></div>

    <header class="header" v-if="!isMobile">
      <h1 class="name">{{ name }}</h1>
      <p class="title">{{ description }}</p>
      <div class="contact-info">
        <ContactLink
          v-for="(contact, index) in contacts"
          :key="index"
          :href="contact.href"
          :imgSrc="contact.imgSrc"
          :alt="contact.alt"
          :text="contact.text"
        />
      </div>
    </header>

    <section class="projects" v-if="!isMobile">
      <h2>Participation projects</h2>
      <ProjectCard
        v-for="(project, index) in projects"
        :key="index"
        :title="project.title"
        :description="project.description"
        :link="project.link"
        :platform="project.platform"
      />
    </section>

    <div class="friends" v-if="!isMobile">
      <h2>Friends</h2>
      <ul class="friends-element">
        <li v-for="(friend, index) in friends" :key="index">
          <a :href="friend.href" target="_blank">{{ friend.name }}</a>
        </li>
      </ul>
      If you wish to exchange friend links, please contact me.
    </div>

    <div class="mobile-layout" v-if="isMobile">
      <header class="mobile-header">
        <h1 class="name">{{ name }}</h1>
        <p class="title">{{ description }}</p>
      </header>

      <div class="mobile-contact">
        <h2>Contact</h2>
        <div>
          <ContactLink
            v-for="(contact, index) in contacts"
            :key="index"
            :href="contact.href"
            :imgSrc="contact.imgSrc"
            :alt="contact.alt"
            :text="contact.text"
          />
        </div>
      </div>

      <section class="mobile-projects">
        <h2>Projects</h2>
        <ProjectCard
          v-for="(project, index) in projects"
          :key="index"
          :title="project.title"
          :description="project.description"
          :link="project.link"
          :platform="project.platform"
        />
      </section>

      <div class="mobile-friends">
        <h2>Friends</h2>
        <ul>
          <li v-for="(friend, index) in friends" :key="index">
            <a :href="friend.href" target="_blank">{{ friend.name }}</a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>


<script>
import ContactLink from './components/ContactLink.vue'
import ProjectCard from './components/ProjectCard.vue'

import githubIcon from './assets/github-icon.svg'
import telegramIcon from './assets/telegram-icon.svg'
import mailIcon from './assets/mail-icon.svg'

export default {
  components: {
    ContactLink,
    ProjectCard,
  },
  data() {
    return {
      name: 'Enlysure',
      description: 'Want to change the world through coding.',
      contacts: [
        {
          href: 'https://github.com/Rovniced',
          imgSrc: githubIcon,
          alt: 'GitHub',
          text: 'Rovniced',
        },
        {
          href: 'https://t.me/luotianyi_2333',
          imgSrc: telegramIcon,
          alt: 'Telegram',
          text: 'Telegram',
        },
        {
          href: 'mailto:enlysure@gmail.com',
          imgSrc: mailIcon,
          alt: 'Mail',
          text: 'Gmail',
        },
      ],
      projects: [
        {
          title: 'ArkLights',
          description: 'The Most Powerful Arknights Gaming Script',
          link: 'https://github.com/AegirTech/ArkLights',
          platform: 'Github',
        },
        {
          title: 'Music Download Bot',
          description: 'A Telegram music download bot',
          link: 'https://t.me/music_v1bot',
          platform: 'Telegram',
        },
        {
          title: 'BiliBili Sticker Transform Bot',
          description:
            'A Telegram bot that converts BiliBili Stickers into Telegram',
          link: 'https://t.me/Enlysure_sticker_bot',
          platform: 'Telegram',
        },
      ],
      friends: [
        { name: '思思', href: 'https://github.com/sisi0318' },
        { name: '叶叶', href: 'https://github.com/leafmoes' },
        { name: '墨缘', href: 'https://github.com/MoYuanCN' },
        { name: '萝莉@TheSw1m', href: 'https://github.com/swim233' },
        { name: 'Ice Elysia', href: 'https://t.me/ice_elysia' },
      ],
      isMobile: false,
    }
  },
  created() {
    this.checkScreenWidth();
    window.addEventListener('resize', this.checkScreenWidth);
  },
  beforeUnmount() {
    window.removeEventListener('resize', this.checkScreenWidth);
  },
  methods: {
    checkScreenWidth() {
      this.isMobile = window.innerWidth < 768;
    },
  }
}
</script>

<style scoped>
:root {
  --main-color: #007acc;
  --text-color: #fff;
  --background-blur: rgba(255, 255, 255, 0.1);
}

.background-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url('@/assets/background.png');
  background-size: cover;
  background-position: center;
  filter: brightness(0.3);
  z-index: -1;
}

.header {
  position: absolute;
  top: 10%;
  left: 5%;
  color: #fff;
}

.name {
  font-size: 3.5em;
  margin: 0;
  font-weight: bold;
}

.title {
  font-size: 1.8em;
  margin: 0;
}

section {
  margin: 20px;
  padding-left: 10px;
}

h2 {
  margin-top: 40px;
  margin-bottom: 20px;
  font-weight: bold;
  color: #fff;
}

.contact-info {
  margin-top: 20px;
}

.contact-info a {
  display: flex;
  align-items: center;
  color: #fff;
  text-decoration: none;
  margin-right: 20px;
  font-size: 1.2em;
}

.projects {
  position: absolute;
  top: 10%;
  right: 10%;
  width: 350px;
}

.friends {
  position: absolute;
  bottom: 10%;
  left: 5%;
  color: #fff;
}

.friends h2 {
  margin: 0 0 10px 0;
  font-weight: bold;
}

.friends ul {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 10px;
  list-style: none;
  padding: 0;
}

.friends li {
  margin-bottom: 0;
}

@media (min-width: 600px) {
  .friends ul {
    grid-template-columns: repeat(2, 1fr);
  }
}

.friends a {
  color: #fff;
  text-decoration: none;
  font-size: 1.2em;
}

.friends a:hover {
  text-decoration: underline;
  background-color: rgba(255, 255, 255, 0.1);
}

.friends-element {
  margin-bottom: 20px;
}

.mobile-layout {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}
.mobile-header {
  font-size: 0.9em;
}

.mobile-header, .mobile-contact, .mobile-projects, .mobile-friends {
  color: #fff;
  margin-bottom: auto;
}

.mobile-contact h2,
.mobile-projects h2,
.mobile-friends h2 {
  font-size: 2em;
  color: #fff;
  width: 100%;
}

.mobile-contact a,
.mobile-friends a {
  color: #fff;
  display: block;
  margin: 5px 0;
}

.mobile-contact a {
  color: #fff;
  display: flex;
  align-items: center;
  margin: 5px 0;
  text-decoration: none;
  padding: 10px;
  box-sizing: border-box;
}

</style>
