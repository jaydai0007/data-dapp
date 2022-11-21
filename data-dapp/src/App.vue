<template>
  <div id = "app">
    @{{user.username}} - {{fullName}}
    <strong>followers:</strong>{{followers}}
    <button @click = "followerUser">
      Follow
    </button>
  </div>
</template>

<script>
export default{
  name:'App',
  data(){
    return{
      isLoading: 0,
      followers: 0,
      user:{
        id: 1,
        username:"jaydai",
        firstName:"Junjie",
        lastName:"Dai",
        email: "jaydai0007@gmail.com",
        isAdmin: true
      }
    }
  },
  watch:{
    followers(newFollowerCount, oldFollowerCount){
      if (oldFollowerCount<newFollowerCount){
        console.log(`${this.user.username} has gained a follower`)
      }
    }
  },
  computed:{
    fullName(){
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  methods:{
    followerUser(){
      this.followers ++
    }
  },
  mounted(){
    this.followerUser();
  }
}


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  text-align: center;
}
</style>
