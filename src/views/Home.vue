<template>
  <div class="home">
    <dm-heading type="h1">Nonononono,</dm-heading>
    <dm-heading type="h1">bueno si.</dm-heading>
    <br>

    <dm-divider size="large"></dm-divider>
    <div v-if="wisdom">
      <dm-heading type="h1">{{ wisdom }}</dm-heading>
      <dm-divider size="large"></dm-divider>
    </div>

    <br>
    <QuestionForm :question.sync="question"/>
    <br>
    <dm-button v-on:click="askQuestion">/Ask</dm-button>
  </div>
</template>

<script>
// @ is an alias to /src
import QuestionForm from '@/components/QuestionForm.vue';

export default {
  name: 'home',
  components: {
    QuestionForm,
  },
  data() {
    return {
      question: '',
      wisdom: false,
    };
  },
  methods: {
    async askQuestion() {
      if (this.question.slice(-1) === '?') {
        const response = await this.axios.get('https://yesno.wtf/api');
        this.wisdom = response.data.answer;
      } else {
        this.wisdom = 'Si no saben preguntar pa que me invitan...';
      }
    },
  },
};
</script>
<style lang="sass">
body
  background-color: #2c3e50
</style>
