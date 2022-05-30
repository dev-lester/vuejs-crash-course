<template>
<div style="margin-top: 20px">
  <form @submit="onSubmit" class="p-formgroup-inline">
    <div class="p-field">
      <label for="name" class="p-sr-only">Name</label>
      <InputText v-model="this.name" id="name" type="text" placeholder="name" />
    </div>
    <div class="p-field">
      <label for="age" class="p-sr-only">Age</label>
      <InputText v-model="this.age" id="age" type="number" placeholder="age" />
    </div>
    <div class="p-field">
      <label for="url" class="p-sr-only">URL</label>
      <InputText v-model="this.url" id="url" type="text" placeholder="Image URL" />
    </div>
    <Button type="submit" label="Save" />
  </form>
</div>
</template>

<script>
export default {
  name: "AddPet",
  data() {
    return {
      name: "",
      age: "",
      url: ""
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      const newPet = {
        name: this.name,
        age: this.age,
        url: this.url,
        isFavorite: false
      }
      // console.log("New Pet Added!", newPet);
      this.$emit("add-pet", newPet);
      this.name = ""
      this.age = ""
      this.url = ""

    }
  }
}
</script>

<style>

</style>