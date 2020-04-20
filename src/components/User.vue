<template>
  <div class="card">
    <v-card outlined>
      <v-card-title>
        <v-avatar size="120">
          <img class="avatar" v-bind:src="user.picture.large" alt="User photo" />
        </v-avatar>
        <h2 class="display-1">{{user.name}}</h2>
      </v-card-title>
      <v-card-text>
        <div class="grid title">
          <div>Gender:</div>
          <div class="font-weight-light gender">{{user.gender}}</div>
          <div>Date of birth:</div>
          <div class="font-weight-light">{{new Date(user.dob).toDateString()}}</div>
          <div>Email:</div>
          <div class="font-weight-light">{{user.email}}</div>
          <div>Phone:</div>
          <div class="font-weight-light">{{user.phoneNumber}}</div>
          <div>Country:</div>
          <div class="font-weight-light">{{user.address.country}}</div>
          <div>City:</div>
          <div class="font-weight-light">{{user.address.city}}</div>
          <div>Address:</div>
          <div class="font-weight-light">{{`${user.address.street}, ${user.address.postcode}`}}</div>
        </div>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  props: ["user"]
};
</script>


<style lang="scss" scoped>
.v-card {
  padding: 30px 50px 50px 50px;
}

.v-card__title {
  display: flex;
  padding-bottom: 2rem;

  h2 {
    padding-left: 3rem;
  }
}

.gender {
  text-transform: capitalize;
}

.card {
  max-width: 630px;
  min-width: 300px;
  margin: auto;
}

.grid {
  display: grid;
  grid-template-columns: 5fr 7fr;
}
</style>


