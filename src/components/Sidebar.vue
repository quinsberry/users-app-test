<template>
  <v-card height="100%" width="256" class="mx-auto">
    <v-navigation-drawer permanent>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="headline font-regular">Users list</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense v-if="this.loading">
        <v-list-item v-for="i in 20" :key="i">
          <v-list-item-icon>
            <Loader />
          </v-list-item-icon>
          <v-list-item-content class="loading-content"></v-list-item-content>
        </v-list-item>
      </v-list>

      <v-list dense v-else>
        <v-list-item v-for="(user, i) in this.users" :key="i" link @click="selectUser(user)">
          <v-list-item-icon>
            <v-avatar size="35">
              <img class="avatar" v-bind:src="user.picture.medium" alt="User photo" />
            </v-avatar>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{`${user.name.first} ${user.name.last}`}}</v-list-item-title>
            <v-list-item-subtitle>{{`user id: ${i+1}`}}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-card>
</template>

<script>
import Loader from "@/components/Loader";

export default {
  props: ["users", "loading"],
  components: {
    Loader
  },
  methods: {
    selectUser(userInfo) {
      const { gender, name, dob, email, phone, location, picture } = userInfo;
      const obj = {
        gender: gender,
        name: `${name.first} ${name.last}`,
        dob: dob.date,
        email: email,
        phoneNumber: phone,
        address: {
          country: location.country,
          street: `${location.street.number} ${location.street.name}`,
          city: location.city,
          postcode: location.postcode
        },
        picture: picture
      };
      this.$emit("select-user", obj);
    }
  }
};
</script>

<style lang="scss" scoped>
.headline {
  padding-left: 1rem;
}

.list-descr {
  height: 40px !important;
}

.loading-content {
  margin-top: 10px;
  height: 40px;
  border-radius: 10px;
  background-color: hsl(0, 0%, 96%);
}
</style>