<script>
    export default {
        data(){
            return {
                currentValue: "",
                tags:[],
            }
        },
        methods:{
            setCurrentValue(){
                this.currentValue = "hola"
            },
            handleSubmit(e){
                const exist = this.tags.some((item) => item === this.currentValue);
                if(exist){
                    this.deletedTag(this.currentValue);
                }

                if(this.currentValue !== ""){
                    this.tags.push(this.currentValue);
                    this.currentValue = "";
                }
           },
           handleClick(){
            if(this.currentValue !== ""){
                    this.tags.push(this.currentValue);
                    this.currentValue = "";
            }
           },
           deletedTag(tag){
            this.tags = this.tags.filter((item) => item !== tag);
           }
        }

    }
</script>

<template>
    <div class="input-tag">
        <div class="tags">
            <div class="tag" v-for="(tag,index) in tags" :key="index">
                {{ tag }} <button @click="deletedTag(tag)">X</button>
            </div>
        </div>
        <form @submit.prevent="handleSubmit" action="">
            <input type="text" v-model="currentValue" />
        </form>
        <div>
            {{ currentValue }}
        </div>
        <button @click="handleClick">
            Agregar
        </button>
    </div>
</template>

<style scoped>
</style>