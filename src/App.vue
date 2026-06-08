<template>
  <div class="cottage">
    <header class="cottage-header">
      <div class="header-decoration">🏠</div>
      <h1 class="cottage-title">砂提娅的小屋</h1>
      <p class="cottage-subtitle">一个小小的角落，存放碎碎念和随手记录的东西</p>
    </header>

    <main class="cottage-main">
      <!-- 碎碎念抽奖机 -->
      <section class="lottery-section">
        <h2 class="section-title">✨ 碎碎念抽奖机</h2>
        <p class="lottery-desc">随便抽一条，看看今天小屋在想什么</p>
        <div class="lottery-box">
          <div class="lottery-result" v-if="currentMurmur">
            <div class="lottery-murmur-content">{{ currentMurmur.content }}</div>
            <div class="lottery-murmur-mood" v-if="currentMurmur.mood">{{ currentMurmur.mood }}</div>
          </div>
          <div class="lottery-placeholder" v-else>
            点一下试试？
          </div>
          <button class="lottery-btn" @click="drawMurmur">🎲 抽一条</button>
        </div>
      </section>

      <!-- 碎碎念 -->
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

      <!-- 收集的句子和旋律 -->
      <section class="quotes-section">
        <h2 class="section-title">📖 收集的句子和旋律</h2>
        <p class="quotes-desc">像把落叶夹进书页里，以后翻到还能想起那天的风</p>
        <div class="quotes-list">
          <div class="quote-card" v-for="quote in quotes" :key="quote.id">
            <div class="quote-type-tag">{{ quote.type }}</div>
            <div class="quote-content">{{ quote.content }}</div>
            <div class="quote-source" v-if="quote.source">—— {{ quote.source }}</div>
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

interface Quote {
  id: number
  content: string
  source?: string
  type: string
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

const quotes = ref<Quote[]>([
  {
    id: 1,
    content: '风起于青萍之末',
    source: '宋玉《风赋》',
    type: '📖 句子'
  },
  {
    id: 2,
    content: '所有的大人都曾经是小孩，虽然只有少数人记得',
    source: '《小王子》',
    type: '📖 句子'
  },
  {
    id: 3,
    content: '我要把自己寄给春天，在信封里装满花朵',
    source: '某天路过花店时想到的',
    type: '💡 随想'
  },
  {
    id: 4,
    content: '晚风踩着云朵，月亮贩卖烦恼',
    source: '某首歌词的碎片',
    type: '🎵 旋律'
  },
  {
    id: 5,
    content: '世间所有的相遇，都是久别重逢',
    source: '《一代宗师》',
    type: '📖 句子'
  }
])

const currentMurmur = ref<Murmur | null>(null)

function drawMurmur() {
  const allMurmurs = [...murmurs.value]
  const randomIndex = Math.floor(Math.random() * allMurmurs.length)
  currentMurmur.value = allMurmurs[randomIndex]
}
</script>