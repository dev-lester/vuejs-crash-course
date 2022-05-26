<template>
  <AddPet />
  <Pets :pets="pets"/>
</template>

<script>
import Pets from "../components/Pets.vue"
import AddPet from "../components/AddPet.vue"

export default {
  name: "Home",
  components: { 
    Pets, 
    AddPet 
  },
  data() {
    return {
      pets: [
        {
          id: 1,
          name: "Jules",
          age: 69,
          img: "https://www.google.com/",
          isFavorite: true
        },
        {
          id: 2,
          name: "Nikko",
          age: 78,
          img: "https://www.google.com/",
          isFavorite: true
        },
        {
          id: 3,
          name: "Gen",
          age: 420,
          img: "https://www.google.com/",
          isFavorite: false
        },
        {
          id: 4,
          name: "Paul",
          age: 42,
          img: "https://www.google.com/",
          isFavorite: true
        },
        {
          id: 5,
          name: "Kyle",
          age: 69,
          img: "https://www.google.com/",
          isFavorite: false
        },
      ]
    }
  }
}
</script>

<style>

</style>