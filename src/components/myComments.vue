<template>
    <div class="container">
        <h1>Comentários</h1>
        <hr />
        <myFormTODO v-on:add-todo="addComment"></myFormTODO>
        <div class="list-group">
            <p v-if="comments.length<=0">Sem comentários...</p>
            <div class="list-group-item" v-for="(c,index) in allComments" v-bind:key="index">
                <span class="comment__author">Autor: <strong> {{c.name}} </strong></span>
                <p>{{c.message}}</p>
                <a href="#" title="Excluir" v-on:click.prevent="delComment(c.id) ">Excluir</a>
            </div>
        </div>
    </div>
</template>

<script>
    import myFormTODO from './myFormTODO';
    export default{
        components:{
            myFormTODO 
        },
        data(){
            return {
                comments: [],
            }
        },

        methods: {
            addComment(comment){
                this.comments.push(comment);
            },
            delComment(index){
                this.comments = this.comments.filter(comment => comment.index !== index);
            }

        },

        computed: {
            allComments(){
                return this.comments.map(c => ({
                    ...c,
                    name: c.name.trim()==='' ? 'Anônimo' : c.name
                }))
            }
        },

        watch: {
            comments(val) {
                console.log('val', val)
            }
        }
    }

</script>
