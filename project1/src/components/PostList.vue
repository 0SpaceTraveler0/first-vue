<template>
    <div class = 'post' v-for="post in posts">
        <div><strong>Имя:</strong> {{post.name}}</div>
        <div><strong>Телефон:</strong>  {{post.phone}}</div>
        <div><strong>Кем приходиться:</strong>  {{post.body}}</div>
    </div>
</template>
<script>
export default{
    props: {
        posts:{
            type: Array,
            required: true
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
</style>
 