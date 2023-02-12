<script>
import ProgressBar from './components/ProgressBar.vue'
import { ref } from 'vue'
export default {
  components: { ProgressBar },
  setup () {

    const items = ref([
      { label: "Initialisation du test technique", max: 100, value: 50 },
      { label: "Progression du développement", max: 100, value: 25 },
    ]);

    return { items }

  },
  methods: {
    addPercent (value) {
      this.items = this.items.map(item => {

        const newValue = item.value + value;
        return { ...item, value: newValue < 100 ? newValue : 100 }

      })
    },
    reset () {
      this.items = this.items.map(item => ({ ...item, value: 0 }))
    }
  }
}
</script>

<template>
  <h1>Test technique WEB-ATRIO réalisé par Grimbert Jean <br/> réalisé le 12/02/2023</h1>
  <ProgressBar
      v-for="(item) in items"
      :input="item"
  />
  <div class="buttons">
    <button @click="reset()">Remettre à zéro les compteurs</button>
    <button @click="addPercent(5)">Ajouter 5%</button>
    <button @click="addPercent(10)">Ajouter 10%</button>
  </div>
</template>

<style scoped>
h1 {
  text-align: center;
  font-size: 0.999em;
  margin-bottom: 5em;
}
.buttons {
  margin-top: 2.5em;
}
</style>
