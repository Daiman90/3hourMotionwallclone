<template>
    <v-content>
      <Filtering @value="getValue" />
      <Card v-for="result in results" :key="result.document" :result="result" />
      <div class="flex xs12">
        <v-btn @click="getData">
          Load more
        </v-btn>
      </div>
    </v-content>
</template>

<script>
import Card from '@/components/Card';
import Filtering from '@/components/Filtering';

export default {
  data: () => ({
    filtered: 'Recent',
    number: 0,
    results: [],
  }),
  components: {
    Card,
    Filtering
  },
  mounted() {
    this.getData();
  },
  watch: {
    filtered: function() {
      this.filterResults();
    }
  },
  methods: {
    async getData() {
      const response = await fetch(`https://cors-anywhere.herokuapp.com/https://motionwall.it/api/feedWallpapers/${this.number}`);
      const result = await response.json();
      await result.forEach(item => {
        this.results.push(item);
      })
      this.number += 8;
    },
    getValue(value) {
      this.filtered = value
    },
    filterResults() {
      if (this.filtered === 'Recent') {
        for(let i = 0, a = 1; i < this.results.length, a < this.results.length; i++, a++) {
          if(this.results[i].updated > this.results[a].updated && this.results[a] <= this.results.length) {
            [this.results[i], this.results[a] = this.results[a], this.results[i]]
          }
        }
      } else if (this.filtered === 'Most downloaded') {
        for(let i = 0, a = 1; i < this.results.length, a < this.results.length; i++, a++) {
          if(this.results[i].downloads > this.results[a].downloads && this.results[a] <= this.results.length) {
            [this.results[i], this.results[a] = this.results[a], this.results[i]]
          }
        }
      } else if (this.filtered === 'Older') {
        for(let i = 0, a = 1; i < this.results.length, a < this.results.length; i++, a++) {
          if(this.results[i].updated < this.results[a].updated && this.results[a] <= this.results.length) {
            [this.results[i], this.results[a] = this.results[a], this.results[i]]
          }
        }
      }
    }
  }
}
</script>
