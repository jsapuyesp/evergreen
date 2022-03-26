<template>
  <b-container>
    <b-form>
      <b-form-group label="Your Name:" label-for="input-1">
        <b-form-input
          v-model="form.name"
          placeholder="Enter name"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Your Number:" label-for="input-2">
        <b-form-input
          v-model="form.number"
          placeholder="Enter number"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group
        label="Email address:"
        label-for="input-3"
        description="We'll never share your email with anyone else."
      >
        <b-form-input
          v-model="form.email"
          type="email"
          placeholder="Enter email"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group label="Gender:" label-for="input-4">
        <b-form-select
          v-model="form.gender"
          :options="genders"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group>
        <label>Birth date:</label>
        <b-form-datepicker
          v-model="form.birthDate"
          class="mb-2"
        ></b-form-datepicker>
      </b-form-group>

      <b-form-group>
        <b-form-checkbox
          v-model="form.sender"
          @click="form.sender = !form.sender"
          >Sender</b-form-checkbox
        >
        <b-form-checkbox
          v-model="form.receiver"
          @click="form.receiver = !form.receiver"
          >Receiver</b-form-checkbox
        >
      </b-form-group>

      <b-button variant="primary" @click="createUser">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <div class="mt-5">
      <b-table :items="items"> </b-table>
    </div>
  </b-container>
</template>

<script>
export default {
  async mounted() {
    await this.getUsers();
  },
  data() {
    return {
      items: [],
      form: {
        name: "",
        gender: null,
        email: "",
        number: "",
        birthDate: "",
        sender: false,
        receiver: false,
      },
      genders: [
        { text: "Select One", value: null },
        { text: "Male", value: "male" },
        { text: "Female", value: "female" },
        { text: "Other", value: "other" },
      ],
    };
  },
  methods: {
    createUser() {
      return this.$axios.post("http://18.209.47.117/users", {
        name: this.form.name,
        gender: this.form.gender,
        email: this.form.email,
        number: this.form.number,
        birth_date: this.form.birthDate + "T00:00:00",
        sender: this.form.sender,
        receiver: this.form.receiver,
      });
    },
    async getUsers() {
      await this.$axios.get("http://18.209.47.117/users").then((response) => {
        this.items = response.data;
      });
    },
  },
};
</script>
