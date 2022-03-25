<template>
  <b-container>
    <b-form>
      <b-form-group id="input-group-1" label="Your Name:" label-for="input-1">
        <b-form-input
          id="input-1"
          v-model="form.name"
          placeholder="Enter name"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Your Number:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.number"
          placeholder="Enter number"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group
        id="input-group-3"
        label="Email address:"
        label-for="input-3"
        description="We'll never share your email with anyone else."
      >
        <b-form-input
          id="input-3"
          v-model="form.email"
          type="email"
          placeholder="Enter email"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-4" label="Gender:" label-for="input-4">
        <b-form-select
          id="input-4"
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

      <b-form-group id="input-group-5">
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

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
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
};
</script>
