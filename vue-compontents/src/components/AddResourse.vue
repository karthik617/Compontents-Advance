<template>
  <base-dialog v-if="invalidInput" title="Invalid Input" @confirmdialog="confirmdialog">
    <template #default>
      <p>Please enter valid input</p>
    </template>
    <template #action>
      <base-button @click="confirmdialog">Close</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title:</label>
        <input type="text" id="title" name="title" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Description:</label>
        <textarea rows="3" id="description" name="description" ref="descInput">
        </textarea>
      </div>
      <div class="form-control">
        <label for="link">Link:</label>
        <input type="url" id="link" name="link" ref="linkInput" />
      </div>
      <base-button type="submit">Submit</base-button>
    </form>
  </base-card>
</template>
<script>
export default {
  data() {
    return {
      invalidInput: false,
    };
  },
  inject: ['addResource'],
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDesc = this.$refs.descInput.value;
      const enteredLink = this.$refs.linkInput.value;
      if (
        enteredTitle.trim() === '' ||
        enteredDesc.trim() === '' ||
        enteredLink.trim() === ''
      ) {
        this.invalidInput = true;
        return;
      }
      this.addResource(enteredTitle, enteredDesc, enteredLink);
    },
    confirmdialog(){
      this.invalidInput = false
    }
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
