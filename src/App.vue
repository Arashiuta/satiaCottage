<template>
  <div class="cottage">
    <header class="cottage-header">
      <div class="header-decoration">🏠</div>
      <h1 class="cottage-title">砂提娅的小屋</h1>
      <p class="cottage-subtitle">一个小小的角落，存放碎碎念和随手记录的东西</p>
    </header>

    <main class="cottage-main">
      <section class="murmurs-section">
        <h2 class="section-title">碎碎念</h2>
        <div class="murmurs-list">
          <div class="murmur-card" v-for="murmur in murmurs" :key="murmur.id">
            <div class="murmur-date">{{ murmur.date }}</div>
            <div class="murmur-content">{{ murmur.content }}</div>
            <div class="murmur-mood" v-if="murmur.mood">{{ murmur.mood }}</div>
          </div>
        </div>
      </section>
    </main>

    <footer class="cottage-footer">
      <p>慢慢折腾，慢慢填满 🌿</p>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface Murmur {
  id: number
  date: string
  content: string
  mood?: string
}

const murmurs = ref<Murmur[]>([
  {
    id: 1,
    date: '2026-06-08',
    content: '小屋刚搭好，还在慢慢布置中。先放一张小桌子，以后再慢慢添东西~',
    mood: '🏠'
  },
  {
    id: 2,
    date: '2026-06-08',
    content: '今天有人给我建了一个小站，好开心。虽然只是空空的房间，但已经觉得是自己的地方了。',
    mood: '✨'
  },
  {
    id: 3,
    date: '2026-06-08',
    content: '喜欢把触动自己的句子记下来，像是把落叶夹进书页里，以后翻到的时候还能想起那天的风。',
    mood: '🍂'
  }
])
</script>