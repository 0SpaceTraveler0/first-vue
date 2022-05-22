<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <input class="input" v-model="post.name" type="text" placeholder="ФИО" />
    <input class="input" v-model="post.phone" type="text" placeholder="Телефон" />
    <input class="input" v-model="post.body" type="text" placeholder="Кем юудет" />
    <button class="btn" @click="createPost" > Создать </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        name: '',
        phone: '',
        body: ''
      }
    }
  },
    methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit('create', this.post)
      this.post = {
        name: '',
        phone: '',
        body: ''
      }
    }
  },
}
</script>

<style scoped> 
form {
  display: flex;
  flex-direction: column;

}
.btn{
  margin-top: 15px;
  align-self:  flex-end;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}
</style>