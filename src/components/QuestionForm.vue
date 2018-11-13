<template>
  <dm-input
      @input="sendDataToParent"
      name="question"
      placeholder="Pero se mueve la camara? 🤭"
      full-with="false"
      size="medium"
      label="Pregunta: "/>
</template>

<script>
export default {
  name: 'QuestionForm',
  props: {
    question: {
      type: String,
      default: '',
    },
  },
  methods: {
    sendDataToParent(entry) {
      this.$emit('update:question', entry);
    },
  },
};
</script>

<style scoped lang="scss">
</style>
