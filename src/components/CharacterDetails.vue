<template lang="html">
    <div v-if="character">
        <h3>{{character.name}}</h3>
        <p>Status: {{character.status}}</p>
        <p>Species: {{character.species}}</p>
    </div>
    <div v-else="!character">
        <p>Please select a character</p>
    </div>
</template>

<script>

export default {
  name: 'character-detail',
  props: ['character']
}

</script>

<style lang="css" scoped>

</style>
