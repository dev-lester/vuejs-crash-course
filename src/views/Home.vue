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
    async addPet(pet) {
      const res = await fetch("https://62942560a7203b3ed0636f3c.mockapi.io/pets", {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify(pet)
      });

      const data = await res.json(); 
      this.pets = [...this.pets, data]
    },

    async removePet(id) {
      if (confirm("Are you sure you want to remove")) {
        const res = await fetch(
          `https://62942560a7203b3ed0636f3c.mockapi.io/pets/${id}`,
          {
            method: "DELETE",
          }
        );
        res.status === 200 
        ? this.pets = this.pets.filter((pet) => pet.id !== id) 
        : alert('Failed to delete Pet!');
      }
    },

    async addFavorite(id) {
      const addFavorite = await this.fetchPet(id);
      const updatedFavorite = {
        ...addFavorite, 
        isFavorite: !addFavorite.isFavorite
      };
      const res = await fetch(`https://62942560a7203b3ed0636f3c.mockapi.io/pets/${id}`, 
      {
        method: "PUT",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify(updatedFavorite)
      });
      const data = await res.json()
      this.pets = this.pets.map((pet) => pet.id === id ? {...pet, isFavorite: data.isFavorite} : pet)
    },

    async fetchPets() {
      const res = await fetch(
        "https://62942560a7203b3ed0636f3c.mockapi.io/pets"
      );
      const data = await res.json();
      return data;
    },

    async fetchPet(id) {
      console.log("fetch pet", id)
      const res = await fetch(`https://62942560a7203b3ed0636f3c.mockapi.io/pets/${id}`);
      const data = await res.json();
      console.log({data})
      return data;
    }
    
  },
  data() {
    return {
      pets: []
    };
  },
  async created() {
    this.pets = await this.fetchPets();

  },
}
</script>

<style>
img {
  height: 250px;
  object-fit: cover;
}

</style>