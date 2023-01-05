<script setup></script>

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
      <input type="password" />
      <p id="error"></p>
      <button type="button">Afficher le nombre de caractères</button>
    </div>
  </section>

  <section id="exercise2">
    <!-- Créer un système permettant de sélectionner une commande et de l'afficher en temps réel -->
    <div>
      <div class="ingredient">
        <h2>Salades</h2>
        <p>Prix : 1&euro;</p>
        <div class="action">
          <button>-</button>
          <input type="number" value="0" />
          <button>+</button>
        </div>
      </div>
      <div class="ingredient">
        <h2>Tomates</h2>
        <p>Prix : 0.2&euro;</p>
        <div class="action">
          <button>-</button>
          <input type="number" value="0" />
          <button>+</button>
        </div>
      </div>
      <div class="ingredient">
        <h2>Pommes de terre</h2>
        <p>Prix : 0.1&euro;</p>
        <div class="action">
          <button>-</button>
          <input type="number" value="0" />
          <button>+</button>
        </div>
      </div>
      <h1>Ma Commande</h1>
      <ul>
        <li>Salades :</li>
        <li>Tomates :</li>
        <li>Pommes de terre :</li>
      </ul>
      <div></div>
      <p>Total : X&euro;</p>
    </div>
  </section>
  <div></div>
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
