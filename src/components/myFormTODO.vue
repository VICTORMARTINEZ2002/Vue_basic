<template>
    <div class="form-todo form-group">
        <p>
            <input placeholder="Nome" name="nome" class="form-control" v-model="name"/>
        </p>
        <p>
            <textarea placeholder="Comentários" name="comentario" class="form-control" v-model="message"></textarea>
        </p>
        <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
    </div>
</template>

<script>
    export default{
        data(){
            return {
                comments: [],
                name: '',
                message: '',
            }
        },

        methods: {
            addComment(){
                if(this.message.trim()===''){return;}
                this.$emit('add-todo', {
                    name: this.name,
                    message: this.message,
                });
                this.name='';
                this.message='';
            },
        }
    }
</script>