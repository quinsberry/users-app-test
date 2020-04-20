<template>
  <div class="wrapper">
    <div class="mainContent" v-if="user">
      <User v-bind:user="user" />
    </div>
    <div class="no-user-content" v-if="!user">
      <h5 class="display-1 font-weight-light">You've not selected anyone. Please select user.</h5>
    </div>
  </div>
</template>

<script>
import User from "@/components/User";

export default {
  props: ["user"],
  components: {
    User
  }
};
</script>


<style lang="scss" scoped>
.wrapper {
  width: 100%;
  height: 100%;
}

.mainContent {
  padding: 50px;
}

.no-user-content {
  width: 100%;
  height: 100%;
  overflow-y: hidden;

  h5 {
    max-width: 800px;
    margin: auto;
    margin-top: 5rem;
    opacity: 0.8;
  }
}
</style>