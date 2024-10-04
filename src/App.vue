<script setup>
import { ref } from 'vue';

// Определение абзацев с состоянием видимости
const paragraphs = ref([
  {
    text: `
    Out of the night that covers me,
        Black as the pit from pole to pole,
    I thank whatever gods may be
        For my unconquerable soul.`,
    isVisible: true,
  },
  {
    text: `
    In the fell clutch of circumstance
        I have not winced nor cried aloud.
    Under the bludgeonings of chance
        My head is bloody, but unbowed.`,
    isVisible: true,
  },
  {
    text: `
    Beyond this place of wrath and tears
        Looms but the Horror of the shade,
    And yet the menace of the years
        Finds and shall find me unafraid.`,
    isVisible: true,
  },
  {
    text: `
    It matters not how strait the gate,
        How charged with punishments the scroll,
    I am the master of my fate,
        I am the captain of my soul.`,
    isVisible: true,
  },
]);

// Переключение видимости абзаца по данному индексу
const toggleVisibility = (index) => {
  if (index >= 0 && index < paragraphs.value.length) {
    paragraphs.value[index].isVisible = !paragraphs.value[index].isVisible;
  }
};
</script>

<template>
  <main>
    <section class="btnBar">
      <button
        v-for="(paragraph, index) in paragraphs"
        :key="'btn-' + index"
        class="bar"
        @click="toggleVisibility(index)"
      >
      </button>
    </section>
    
    <section class="poem">      
      <h1>Invictus</h1>
      <div class="poemText">
        <!-- Отображение каждого абзаца на основе его видимости -->
        <pre
          v-for="(paragraph, index) in paragraphs"
          :key="'para-' + index"
          v-show="paragraph.isVisible"
          class="paragraf"
        >
          {{ paragraph.text }}
        </pre>
      </div>
    </section>
    
    <section class="name">
      <p>By William Ernest Henley</p>
    </section>
  </main>
</template>
