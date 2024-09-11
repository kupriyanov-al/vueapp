<template>
    
    <div class="card mb-3">
      <div class="card-header">
        {{ nowDate }}
      </div>
      <div class="card-body">
        <h5 class="card-title">{{ head }}</h5>
        <p v-if="isOpen" class="card-text">{{ desc }}</p>
        <button type="button" class="btn btn-outline-primary m-2" @click="isOpen =! isOpen">Показать</button>
        <!-- <button type="button" class="btn btn-outline-danger" @click="delNote(index)">Удалить</button> -->
      </div>
    </div>
    
</template>
<script>
export default {
    props: [
        'head', 
        'desc'
        ],
    data() {
        return {
            isOpen : false,
            nowDate: new Date().toLocaleString(),
        }
    },
}
</script>
<style>
    
</style>