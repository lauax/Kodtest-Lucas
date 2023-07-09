<template>
  <div>
    <UserList :users="typedUsers" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import UserList from "./Userlist.vue";

interface User {
  id: number;
  email: string;
  first_name: string;
  last_name: string;
  avatar: string;
}

export default defineComponent({
  name: "UserList2",
  components: {
    UserList,
  },
  props: {
    users: {
      type: Array as () => unknown[],
      required: true,
    },
  },
  computed: {
    typedUsers(): User[] {
      return this.users as User[];
    },
  },
});
</script>
