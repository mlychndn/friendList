<template>
  <form action="submit" @submit.prevent="submitForm()">
    <div>
      <label for="name">Name</label>
      <input type="text" v-model="insertedName" />
    </div>
    <div>
      <label for="name">Phone</label>
      <input type="tel" v-model="insertedPhone" />
    </div>
    <div>
      <label for="name">Email</label>
      <input type="email" v-model="insertedEmail" />
    </div>
    <div>
      <button type="submit">Add Contact</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ["add-contact"],
  data() {
    return {
      insertedName: "",
      insertedPhone: "",
      insertedEmail: "",
    };
  },
  methods: {
    submitForm() {
      this.$emit(
        "add-contact",
        this.insertedName,
        this.insertedPhone,
        this.insertedEmail
      );
    },
  },
};
</script>

<style>
#app input {
  font: inherit;
  padding: 0.15rem;
}
#app label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
#app form div {
  margin: 1rem 0;
}
</style>
