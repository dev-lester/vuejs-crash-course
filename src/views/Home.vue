<template>
  <AddPet @add-pet="addPet" />
  <Pets 
    @remove-pet="removePet"
    @add-favorite="addFavorite"
    :pets="pets"/>
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
  methods: {
    addPet(pet) {
      this.pets = [...this.pets, pet]
      console.log("receiving event from AddPet component to Home componenet", pet);
    },
    removePet(id) {
      if (confirm("Are you sure you want to remvoe this pet?")) {
        this.pets = this.pets.filter((pet) => pet.id !== id)
      }
    },
    addFavorite(id) {
      this.pets = this.pets.map((pet) =>
        pet.id === id ? { ...pet, isFavorite: !pet.isFavorite } : pet
      );
    },
    
  },
  data() {
    return {
      pets: []
    };
  },
  created() {
    this.pets = [
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
      // {
      //   id: 4,
      //   name: "Paul",
      //   age: 42,
      //   img: "https://www.google.com/",
      //   isFavorite: true
      // },
      // {
      //   id: 5,
      //   name: "Kyle",
      //   age: 69,
      //   img: "https://www.google.com/",
      //   isFavorite: false
      // },
      // {
      //   id: 6,
      //   name: "Jester",
      //   age: 69,
      //   img: "https://www.google.com/",
      //   isFavorite: false
      // },
      // {
      //   id: 7,
      //   name: "Sofia",
      //   age: 69,
      //   img: "https://www.google.com/",
      //   isFavorite: false
      // },
      // {
      //   id: 8,
      //   name: "Nina",
      //   age: 69,
      //   img: "https://www.google.com/",
      //   isFavorite: false
      // }
    ]
  },
}
</script>

<style>

</style>