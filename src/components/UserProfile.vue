<template>
  <div class="userprofile">
    <div class="userpanel">
      <h2 class="username"> @{{user.username}}</h2>
      <div class="user-badge" v-if="user.isAdmin">Admin</div>
      <div class="followpanel">
        <strong>Followers: </strong> {{followers}}
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: "UserProfile",
  data() {
    return {
      followers: 0,
      user: {
        firstname: 'James',
        lastname: 'Damilare',
        username: 'JamesDamilare12',
        email: 'Jayhmz10@gmail.com',
        isAdmin: false
      }
    };
  },
  props: {},

  computed: { 
    fullname(){
      return this.user.firstname + " "+ this.user.lastname
    }
  },
  methods: {
    follow(){
      this.followers++
    }
  },
  watch: {
    followers(newvalue, oldvalue){
      if(oldvalue < newvalue){
        console.log("the user "+this.fullname+" has a new follower!");
      }
    }
  },
  mounted(){
    this.followers();
  }
};
</script>

<style>

.userprofile{
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 3fr;
  padding: 50px 5%;
}
.userpanel{
  box-shadow: 0px 1px 4px 1px;
  background-color: #ffffff;
  display: flex;
  flex-direction: column;
}
.user-badge{
  background: rebeccapurple;
  padding: 0 10px;
  margin-right: auto;
  margin-left: 10px;
  border-radius: 2px;
  font-weight: bold;
  color: white;       
}

</style>