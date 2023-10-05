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
    <div class="inputTag">
        <div class="tags">
            <div class="tag" v-for="(tag,index) in tags" :key="index">
                {{ tag }} <button class="btn-x" @click="deletedTag(tag)">X</button>
            </div>
        </div>
        <form @submit.prevent="handleSubmit" action="">
            <input type="text" v-model="currentValue" />
        </form>
        
        <button class="btn" @click="handleClick">
            Agregar
        </button>
    </div>
</template>

<style scoped>
.inputTag{
    display: inline-flex;
    min-height: 43px;
}

.tags{
    display:flex;
    
    gap: 3px;
    padding: 5px;
}
.tags .tag{
    border:  solid 2px #ccc;
    display: flex;
    padding: 5px;
    align-items: center;
    border-radius: 3px;
    gap: 5px;
}

.inputTag input {
  height: 95%;
  outline: none;
  padding: 0 5px;
}

.btn-x {
  background-color: transparent;
  border: none;
  border-radius: 3px;
}

.btn{
    margin-left:0.5rem;
    padding: 1rem;
    cursor: pointer;
    background: #545454;
    border: none;
    color: aliceblue;
    font-weight: 800;
    border-radius: 3px;
}

.btn-x:hover {
  background-color: #ccc;
}

@media  (max-width: 460px) {
    .inputTag{
        margin: 0;
        padding: 0;
        justify-content: center;
        display: flex;
        flex-direction: column;
        min-height: 43px;
    }
    .inputTag input {
    height: 50px;
    width: 100%;
    outline: none;
    padding: 0 5px;
    }
    .tags .tag{
        justify-content: space-between;

    }

    .tags{
        flex-direction: column;    
    }
}







/*

.inputTag button {
  background-color: transparent;
  border: none;
  border-radius: 3px;
}
.inputTag button:hover {
  background-color: #ccc;
}
*/
</style>