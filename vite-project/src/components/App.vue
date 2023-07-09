<template>
  <div>
    <UserList :users="userList" v-show="selectedNumber === 1" />
    <UserList2 :users="userList2" v-show="selectedNumber === 2" />
    <Page1and2 @select-number="toggleUserList" />
  </div>
</template>

<script lang="ts">
import Page1and2 from './Page1and2.vue';
import UserList from './Userlist.vue';
import UserList2 from './Userlist2.vue';

export default {
  name: 'App',
  components: {
    UserList,
    UserList2,
    Page1and2
  },
  data() {
    return {
      userList: [],
      userList2: [],
      selectedNumber: 1,
    };
  },
  created() {
    // Fetch users from the first API endpoint
    fetch("https://reqres.in/api/users")
      .then((response) => response.json())
      .then((data) => {
        // Extract the user data from the response
        this.userList = data.data;
      })
      .catch((error) => {
        console.error("Error:", error);
      });

    // Fetch users from the second API endpoint
    fetch("https://reqres.in/api/users?page=2")
      .then((response) => response.json())
      .then((data) => {
        // Extract the user data from the response
        this.userList2 = data.data;
      })
      .catch((error) => {
        console.error("Error:", error);
      });
  },
  methods: {
    toggleUserList(number: number) {
      this.selectedNumber = number;
    },
  },
};
</script>
