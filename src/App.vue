<script setup>
import { ref } from 'vue';
import '../src/components/App.css';

const Heading = ref('Your Result');

const Summarys = ref([
  {
    id: 1,
    label: "Reaction",
    points: 20,
    image: "../images/icon-reaction.svg",
    alt: "Reaction"
  },
  {
    id: 2,
    label: "Memory",
    points: 22,
    image: "../images/icon-memory.svg",
    alt: "Memory"
  },
  {
    id: 3,
    label: "Verbal",
    points: 21,
    image: "../images/icon-verbal.svg",
    alt: "Verbal"
  },
  {
    id: 4,
    label: "Visual",
    points: 72,
    image: "../images/icon-visual.svg",
    alt: "Visual"
  }
])
const getAveragePoints = ()=>{
  const totalPoints = Summarys.value.reduce((total, Summary) => 
  (total + Summary.points), 0)
  return Math.floor(totalPoints / Summarys.value.length)
}

const getScorePercentage = () => {
  const totalPoints = Summarys.value.reduce((total, summary) => total + summary.points, 0);
  const percentage = (totalPoints / (Summarys.value.length * 100)) * 100;
  return percentage.toFixed(2);
};

const done = () =>{
  document.write("<h1>We will get back to you soon!!! Thanks for your time<h1>")
}

</script>

<template>
  <div class="container">
    <div class="upper-container">
      <div class="upper-heading">
        <h1>{{ Heading }}</h1>
      <div class="total-result">
        <p>{{ getAveragePoints() }} <span>of 100</span></p>
      </div>
      <div class="congratulations-message">
        <h2>Great</h2>
        <p>You scored higer than {{ getScorePercentage() }}% of the people who have taken these tests.</p>
      </div>
      </div>
    </div>
    <div class="lower-container">
      <h3>Summary</h3>
      <ul>
        <li v-for="Summary in Summarys" :key="Summary.id">
          <img :src="Summary.image" :alt="Summary.alt">
          <p>{{ Summary.label }}</p>
          <p class="points">{{ Summary.points }} <span>/100</span></p>
        </li>
      </ul>
      <button @click="done" href="#">Continue</button>
    </div>
  </div>
</template>

