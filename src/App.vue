<template>
  <div id="app">
    <div class="background-overlay"></div>
    <header class="header">
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

    <section class="projects">
      <h2>Participation projects</h2>
      <ProjectCard
        v-for="(project, index) in projects"
        :key="index"
        :title="project.title"
        :description="project.description"
        :link="project.link"
      />
    </section>

    <div class="friends">
      <h2>Friends</h2>
      <ul class="friends-element">
        <li v-for="(friend, index) in friends" :key="index">
          <a :href="friend.href" target="_blank">{{ friend.name }}</a>
        </li>
      </ul>
      If you wish to exchange friend links, please contact me.
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
          link: 'https://t.me/music_v1bot',
          platform: 'Telegram',
        },
      ],
      friends: [
        { name: '思思', href: 'https://github.com/sisi0318' },
        { name: '叶叶', href: 'https://github.com/leafmoes' },
        { name: '墨缘', href: 'https://github.com/MoYuanCN' },
        { name: '萝莉@TheSw1m', href: 'https://github.com/swim233' },
      ],
    }
  },
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
}

.contact-info {
  margin-top: 20px;
}

.contact-info a {
  display: flex;
  align-items: center;
  color: var(--text-color);
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
  color: var(--text-color);
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
  color: var(--main-color);
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
</style>
