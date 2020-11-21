<template>
    <div :style="inputDiv">
        <form @submit="addTodo">
            <v-text-field 
                flat 
                solo 
                type="text" 
                v-model="title" 
                rounded 
                background-color="#00BFA5"  
                name="title" 
                placeholder="Add Todo..." 
                spellcheck="true">
                <template v-slot:append>
                    <v-btn rounded type="submit" >Submit</v-btn>
                </template>
                </v-text-field>
        </form>
    </div>
</template>

<script>
import uuid from "uuid";
export default {
    name: "AddTodo",
    data() {
        return {
            title: "",
            inputDiv: {
                width: '50%',
                padding: '10px',
                margin: 'auto'
             
            },
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false,
            }
            //Send to parent
            this.$emit('add-todo',newTodo);
            this.title = "";
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }
    input[type="text"] {
        flex: 10;
        padding: 5px;
        
    }
</style>