<template>
   <div>
       <h1>Postagens</h1>
       <div class="row">
           <div class="col-md-10">
               <div class="col-md-2">
                   <router-link :to="{name: 'create'}" class="btn btn-primary">Criar Postagem</router-link>
               </div>
           </div><br />

           <table class="table table-hover">
               <thead>
                   <tr>
                       <th>ID</th>
                       <th>Nome do Item</th>
                       <th>Preço do Item</th>
                       <th>Ações</th>
                   </tr>
               </thead>

               <tbody>
                   <tr v-for="post in posts" :key="post.id">
                       <td>{{post.id}}</td>
                       <td>{{post.title}}</td>
                       <td>{{post.body}}</td>
                       <td>
                           <router-link
                               :to="{name: 'edit', params: {id: post.id}}" class="btn btn-primary">Editar
                           </router-link>
                       </td>
                       <td>
                           <button class="btn btn-danger" @click="deletePost(post.id)">
                               Excluir
                           </button>
                       </td>
                   </tr>
               </tbody>
           </table>
       </div>
   </div>
</template>

<script>
export default {

    data() {
        return {
            posts: []
        }
    },

    created() {
        let uri = 'http://127.0.0.1:8000/api/posts';
        this.axios.get(uri).then(response => {
            this.posts = response.data.data;
        });
    },

    methods: {
        deletePost(id)
        {
            let uri = `http://127.0.0.1:8000/api/post/delete/${id}`;
            this.axios.delete(uri).then(response => {
                this.post.splice(this.posts.indexOf(id), 1);
            });
        }
    }
}
</script>

<style>

</style>
