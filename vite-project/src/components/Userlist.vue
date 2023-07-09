<template>
  <div>
    <div class="user-list">
      <div v-for="user in users" :key="user.id" class="user-card">
        <img class="avatar" :src="user.avatar" alt="Avatar" />
        <p class="user-name">{{ user.first_name }} {{ user.last_name }}</p>
        <a :href="`mailto:${user.email}`" style="text-decoration: none; color: black">
          <p>Contact</p>
        </a>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
interface User {
  id: number;
  email: string;
  first_name: string;
  last_name: string;
  avatar: string;
}

export default {
  name: "UserList",
  props: {
    users: {
      type: Array as () => User[], 
      required: true,
    },
  },
};
</script>

  <style scoped>
  body{
      background-color: white;
  }
  
  .user-list {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      color: black;
      font-family: Montserrat;
    }
    
    .user-card {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      width: 200px; 
      height: 225px; 
      margin: 10px;
      text-align: center;
      background-color: rgb(235, 235, 235);
      border-radius: 10%;
      padding: 10px;
    }
    
    .avatar {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      
    }
    
  .user-name{
      font-weight: bold;
  }
  
  </style>
  