<template>
  <div id="app" class="landing-page">
    <header class="header">
      <h1 class="brand-title">Brumkie 🍪</h1>
      <p class="tagline">¡Las galletas más deliciosas y únicas están aquí!</p>
    </header>

    <main>
      <section class="about">
        <h2>¿Por qué Brumkie?</h2>
        <p>
          En Brumkie 🍪, nos apasiona hacer galletas irresistibles. Ingredientes
          frescos, sabores únicos y amor en cada mordida.
        </p>
        <img src="https://mandolina.co/wp-content/uploads/2023/06/galletas-chispas-de-chocolate.jpg" alt="Galletas Brumkie" />
      </section>

      <section class="products">
        <h2>Nuestros Sabores</h2>
        <div class="product-list">
          <div class="product-card" v-for="(product, index) in products" :key="index">
            <img :src="product.image" :alt="product.name" />
            <h3>{{ product.name }}</h3>
            <p>{{ product.description }}</p>
            <button @click="addToCart(product)">Comprar - ${{ product.price }}</button>
          </div>
        </div>
      </section>

      
    </main>

    <footer class="footer">
      <p>&copy; 2024 Brumkie 🍪 - Todos los derechos reservados.</p>
    </footer>

    <!-- Burbuja de chat -->
    <div class="chat-bubble" @click="openChat">
      💬
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      products: [
        {
          name: "Red velvet",
          description: "Galletas clásicas con chispas de chocolate blanco.",
          price: 10,
          image: "https://www.gourmet.cl/wp-content/uploads/2023/11/GALLETAS-RED-VELVET.jpg",
        },
        {
          name: "Nutella",
          description: "¡Una explosión de chocolate en cada bocado!",
          price: 12,
          image: "https://i.ytimg.com/vi/uqtMi_AUN7U/maxresdefault.jpg",
        },
        {
          name: "Chip de Chocolate",
          description: "Delicada mezcla de chocolate y Chip crocantes.",
          price: 11,
          image: "https://recetasdecocina.elmundo.es/wp-content/uploads/2015/09/cookies-receta.jpg",
        },
        {
          name: "Kinder",
          description: "El balance perfecto entre dulce y cremoso.",
          price: 13,
          image: "https://img-global.cpcdn.com/recipes/1cc03782f86a6ca7/640x640sq70/photo.webp",
        },
        {
          name: "Lemon Pie",
          description: "El delicioso sabor a limon con lo cremoso del Pie.",
          price: 14,
          image: "https://i.ytimg.com/vi/nI0gUtZzgkY/hq720.jpg?sqp=-oaymwEhCK4FEIIDSFryq4qpAxMIARUAAAAAGAElAADIQj0AgKJD&rs=AOn4CLABfAcp3eybgYwuQgUHWWEmqJ8Glg",
        },
        {
          name: "Nucita",
          description: "Clásicas galletas de nucita con un toque especial.",
          price: 9,
          image: "https://s1.elespanol.com/2023/04/09/cocinillas/recetas/postres/754934523_232288663_1024x576.jpg",
        },
        {
          name: "Queso crema",
          description: "Un sabor exótico y sofisticado.",
          price: 15,
          image: "data:image/jpeg;base64,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",
        },
       
      ],
    };
  },
  methods: {
    addToCart(product) {
      alert(`¡Has agregado "${product.name}" al carrito!`);
    },
    openChat() {
      window.open("https://cm3kmtj8100030jjofqe3dn7y.zapier.app", "_blank");
    },
  },
};
</script>

<style scoped>
/* Estilos básicos */
body {
  font-family: "Arial", sans-serif;
  margin: 0;
  padding: 0;
  color: #333;
}

.landing-page {
  text-align: center;
}

.header {
  background-color: #152148;
  color: white;
  padding: 20px;
}

.brand-title {
  font-size: 2.5em;
  margin: 0;
}

.tagline {
  font-size: 1.2em;
  font-weight: 300;
}

.about img {
  margin-top: 10px;
  max-width: 100%;
  height: auto;
}

.products {
  background: #fff3e0;
  padding: 20px 0;
}

.product-list {
  display: flex;
  justify-content: center;
  gap: 20px;
  flex-wrap: wrap;
}

.product-card {
  background: white;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 15px;
  max-width: 200px;
  text-align: center;
}

.product-card img {
  max-width: 100%;
  height: auto;
}

.product-card button {
  background-color: #152148;
  color: white;
  border: none;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
}

.contact {
  background: #f7f7f7;
  padding: 20px 0;
}

.whatsapp-button {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  text-decoration: none;
  color: #25d366;
  font-weight: bold;
}

.footer {
  background: #333;
  color: white;
  padding: 10px 0;
}

/* Burbuja de chat */
.chat-bubble {
  position: fixed;
  bottom: 20px;
  right: 20px;
  background: #25d366;
  color: white;
  font-size: 1.5em;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  cursor: pointer;
}

.chat-bubble:hover {
  background: #1caa52;
}
</style>
