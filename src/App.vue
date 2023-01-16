<script setup>
import { computed, reactive } from "vue";

const state = reactive({
  password: "",
  currency: {
    name: "Euro",
    symbol: "€",
  },
  vegetables: [
    {
      name: "Beans",
      price: 1,
      quantity: 0,
    },
    {
      name: "Tomatoes",
      price: 0.2,
      quantity: 0,
    },
    {
      name: "Potatoes",
      price: 0.1,
      quantity: 0,
    },
  ],
});

const displayAlert = () => {
  alert(
    `Votre mot de passe possède ${passwordLength.value} caractère${
      passwordLength.value > 1 ? "s" : ""
    }`
  );
  state.password = "";
};

const minusOne = (index) => {
  let quantity = state.vegetables[index].quantity;
  state.vegetables[index].quantity = quantity < 1 ? 0 : --quantity;
};

const passwordLength = computed(() => {
  return state.password.length;
});

const isPasswordValid = computed(() => {
  return passwordLength.value < 10
    ? "Mot passe trop court"
    : "Mot de passe valide";
});

const total = computed(() => {
  // let total = 0;
  // state.vegetables.forEach((v) => {
  //   total += v.quantity * v.price;
  // });
  // return total;
  return state.vegetables.reduce((reducer, v) => {
    return reducer + v.quantity * v.price;
  }, 0);
});
</script>

<template>
  <section id="exercise">
    <!-- 
        - Ecouter la valeur de l'input
        - Afficher "Mot de passe trop court" si le mot de passe est inférieur à 10 caractères, sinon afficher "Mot de passe valide" dans #error.
        - Ecouter la propriété "keydown" et si l'utilisateur appuie sur Enter ou clique sur le bouton, il faut :
                - afficher une alerte avec la longueur du mot de passe ("Votre mot de passe possède X caractères")
                - réinitialiser l'input à la valeur de départ
    -->
    <div>
      <input
        v-model="state.password"
        type="password"
        @keydown.enter="displayAlert"
      />
      <p id="error">{{ isPasswordValid }}</p>
      <button type="button" @click="displayAlert">
        Afficher le nombre de caractères
      </button>
    </div>
  </section>

  <section id="exercise2">
    <!-- Créer un système permettant de sélectionner une commande et de l'afficher en temps réel -->
    <div>
      <div
        v-for="(vegetable, index) of state.vegetables"
        class="ingredient"
        :key="index"
      >
        <h2>{{ vegetable.name }}</h2>
        <p>Prix : {{ vegetable.price }}{{ state.currency.symbol }}</p>
        <div class="action">
          <button @click="minusOne(index)">-</button>
          <input type="number" v-model="vegetable.quantity" />
          <button @click="vegetable.quantity++">+</button>
        </div>
      </div>

      <h1>Ma Commande</h1>
      <ul>
        <li v-for="(vegetable, index) of state.vegetables" :key="index">
          {{ vegetable.name }} : {{ vegetable.quantity }}
        </li>
      </ul>
      <div></div>
      <p>Total : {{ total }} {{ state.currency.symbol }}</p>
    </div>
  </section>
</template>

<style scoped>
section {
  margin-bottom: 50px;
}

.ingredient h2 {
  display: block;
  width: 100%;
}
.ingredient .action {
  display: flex;
}
#exercise2 input {
  text-align: center;
}
</style>
