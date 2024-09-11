<template>
    
    <div class="card mb-3">
      <div class="card-header">
        {{ nowDate }}
      </div>
      <div class="card-body">
        <h5 class="card-title">{{ head }}</h5>
        <p v-if="isNodeOpen" class="card-text">{{ desc }}</p>
        <button type="button" class="btn btn-outline-primary m-2" @click="open">Показать</button>
        <!-- <button type="button" class="btn btn-outline-danger" @click="delNote(index)">Удалить</button> -->
      </div>
    </div>
    
</template>
<script>
export default {
    props: {
        head: {
            type:String,
            required: true
        },
        desc: {
            type: String,
            required: true
        },
        id: {
            type: Number,
            required:true
        },
        isOpen: {
            type: Boolean,
            required:false,
            default: false
        }        
    },
        
    data() {
        return {
            isNodeOpen : this.isOpen,
            nowDate: new Date().toLocaleString(),
        }
    },

    methods: {
        open() {
            this.isNodeOpen =! this.isNodeOpen
            
        }
    }
}
</script>
<style>
    
</style>