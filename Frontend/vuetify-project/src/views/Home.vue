<template>
  <div>
    <v-app-bar>
      <v-container>
        <div class="text-left"> 
          <v-img
          max-width="200"
          src="@/assets/MyNoteHub.png"
          ></v-img>
        </div>
      </v-container>
      <v-btn
        class="ma-2"
        color="error"
        >
          Logout
          <v-icon
            end
            icon="mdi-logout"
          ></v-icon>
        </v-btn>
    </v-app-bar>
    <ToDoList />
  </div>
</template>

<script>
import ToDoList from "@/components/ToDoList.vue"

export default {
  name: 'HomeVue',
  components: {
    ToDoList
  }
}
</script>

<style scoped>
v-btn {
  background-color: blue;
  color: white;
}
</style>
