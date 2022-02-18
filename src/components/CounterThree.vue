<template>
    <form class="form" action="">
      <label>Counter Third:</label>
      <div class="d-flex">
        <input type="text" placeholder="Third Counter" :value="value" disabled>
        <button type="button" class="btn btn-primary ms-5" @click="$emit('onClick',1)">
          <i class="fas fa-plus"></i>
        </button>
        <button type="button" class="btn btn-danger ms-2" @click="$emit('onClick',-1)">
          <i class="fas fa-minus"></i>
        </button>
        <input type="text" placeholder="Name" class="right" :value="getName" @input="$emit('retName',$event)">
      </div>
    </form>
</template>

<script>
export default {
  name: 'CounterThree',
  props: [
    'value',
    'getName'
  ]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
