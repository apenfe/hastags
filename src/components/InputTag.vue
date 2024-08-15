<template>

    <div class="inputTag">

        <div class="tags">

            <div class="tag" v-for="(tag, index) in tags" :key="index">
                {{ tag }} <button @click="deleteTag(tag)">x</button>
            </div>

        </div>

        <input type="text" v-model="currentValue" @keydown="handleKeyDown">

    </div>

</template>

<script>

export default {

    emits: ["onTagsChange"],

    data(){

        return{
            currentValue: "",
            tags: [],
        };

    },
    methods:{

        handleKeyDown(e){

            if(e.key == "Enter" && this.currentValue != ""){

                const exists = this.tags.some(item => item == this.currentValue);

                if(!exists){
                    this.tags.push(this.currentValue);
                    this.currentValue="";
                    this.$emit('onTagsChange',this.tags);
                }

            }else if(e.key == "Backspace" && this.currentValue == ""){
                this.tags.pop();
                this.$emit('onTagsChange',this.tags);
            }

        },

        deleteTag(tag){
           this.tags = this.tags.filter((item) => item != tag);
           this.$emit('onTagsChange',this.tags);
        }

    }

}

</script>

<style scoped>

.inputTag{
    
    display: inline-flex;
    min-width: 300px;
    border: 1px solid #000;
    border-radius: 10px;
    height: 43px;
    box-shadow: 2px 5px 4px rgb(248, 248, 124);
    background: white;
}

.tags{
    display: flex;
    flex-direction: row;
    gap: 5px;
    padding: 5px;
}

.tags .tag{
    display: flex;
    padding: 5px;
    border: solid 1px #ccc;
    gap: 5px;
    align-content: center;
    border-radius: 15px;
    font-size: 12px;
    font-weight: 600;
    text-transform: uppercase;
    line-height: 23px;

}

input{
    display: inline-flex;
    outline: none;
    border: none;
    padding: 0.5px;
    border-radius: 15px;
}

.inputTag button{
    background-color: transparent;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

.inputTag button:hover{
    background-color: rgb(255, 94, 94);
}

</style>