<template>
    <div class = 'post' v-for="post in posts" :key="post">
        <div><strong>Имя:</strong> {{post.name}}</div>
        <div><strong>Телефон:</strong>  {{post.phone}}</div>
        <div><strong>Кем приходиться:</strong>  {{post.body}}</div>
        <button class="btn" @click="deletePost(post)">Удалить</button>
        <button class="btn">Редактировать</button>
    </div> 
</template>
<script>  
export default{
    props: {
        posts:{
            type: Array,
            required: true
        }
    },
    methods:{
        deletePost(post){
            this.$emit('delete', post) 
        }
    }
}
</script>
<style scoped>
.post{
    margin: 5px;
    padding: 15px;
    border: 2px solid teal;    
}
.btn{
    margin: 15px 2px;
    align-self:  flex-end;
    padding: 10px 15px;
    background: none;
    color: teal;
    border: 1px solid teal;
}
.btn:hover{
    background: teal;
    color: white;
}
</style>
 