<template>
  <header><h1>My Friends</h1></header>
  <new-friend @add-contact="addContact"></new-friend>
  <ul>
    <friend-contact
      v-for="friend in friends"
      :key="friend.id"
      :id="friend.id"
      :name="friend.name"
      :phone-number="friend.phone"
      :email-address="friend.email"
      :is-favorite="friend.isFavorite"
      @toggle-favorite="friendToggleFavorite"
      @delete-friend="deleteFriend"
    ></friend-contact>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      friends: [
        {
          id: "manuel",
          name: "Manuel Lorenz",
          phone: "0123 4567 890",
          email: "manuel@localhost.com",
          isFavorite: true,
        },
        {
          id: "julie",
          name: "Julie Jones",
          phone: "9876 5432 10",
          email: "julie@localhost.com",
          isFavorite: true,
        },
      ],
    };
  },
  methods: {
    friendToggleFavorite(friendId) {
      const friends = this.friends.find((friend) => friendId === friend.id);
      friends.isFavorite = !friends.isFavorite;
    },
    addContact(name, phone, email) {
      console.log(name, phone, email);
      const newFriendContact = {
        id: new Date().toISOString(),
        name,
        phone,
        email,
        isFavorite: false,
      };
      console.log(newFriendContact);
      this.friends.push(newFriendContact);
    },
    deleteFriend(friendId) {
      console.log(friendId);
      const friendlist = this.friends.filter(
        (friend) => friendId !== friend.id
      );
      this.friends = friendlist;
    },
  },
};
</script>
