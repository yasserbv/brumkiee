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
          name: "Queso crema y Arequipe",
          description: "Un sabor exótico y sofisticado.",
          image: "https://lasoleta.com/wp-content/uploads/elementor/thumbs/1-1-p5hlcfttph4h2htt3r1tn16b53d3wf1yxwjzgwks5k.png",
        },
       
      ],
    };
  },
  methods: {
    addToCart(product) {
      alert(`¡Has agregado "${product.name}" al carrito!`);
    },
    openChat() {
      window.open("https://brumkie.zapier.app", "_blank");
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
