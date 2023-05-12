<script setup>
import { ref, computed } from 'vue'

const mostrarDiv = ref(false)

const produtos = ref([
  {
    id: 1,
    nome: 'Camiseta',
    preco: 49.9,
    quant: 1,
    img: 'https://d2p7wtszppk2p4.cloudfront.net/Custom/Content/Products/55/19/55191_camisa-1-corinthians-jogador-pr-7852-cv7855100_m2_637818328664576428.jpg'
  },
  {
    id: 2,
    nome: 'Calça',
    preco: 99.9,
    quant: 1,
    img: 'https://static.shoptimao.com.br/produtos/calca-moletom-corinthians-juvenil-phillip/06/D65-2254-006/D65-2254-006_zoom1.jpg?ts=1564482873&ims=544x'
  },
  {
    id: 3,
    nome: 'Meia',
    preco: 9.9,
    quant: 1,
    img: 'https://images-americanas.b2w.io/produtos/1517617581/imagens/meiao-infantil-corinthians-preto-oficial/1517617599_1_large.jpg'
  },
  {
    id: 4,
    nome: 'Sapato',
    preco: 199.9,
    quant: 1,
    img: 'https://static3.tcdn.com.br/img/img_prod/311840/tenis_corinthians_street_preto_e_branco_86854_1_20201130180734.jpg'
  },
  {
    id: 5,
    nome: 'Boné',
    preco: 29.9,
    quant: 1,
    img: 'https://static.netshoes.com.br/produtos/bone-nike-corinthians-aba-curva/26/D12-8176-026/D12-8176-026_zoom1.jpg?ts=1603734784&ims=544x'
  },
  {
    id: 6,
    nome: 'Óculos',
    preco: 99.9,
    quant: 1,
    img: 'https://sportscenter.loja2.com.br/img/ba01929694145290234d80ee63a933a4.png'
  },
  {
    id: 7,
    nome: 'Relógio',
    preco: 299.9,
    quant: 1,
    img: 'https://static.shoptimao.com.br/produtos/relogio-corinthians-technos-analogico-masculino/06/F61-1223-006/F61-1223-006_zoom1.jpg?ts=1603733030'
  },
  {
    id: 8,
    nome: 'Bermuda',
    preco: 79.9,
    quant: 1,
    img: 'https://imgs.casasbahia.com.br/1544057339/1xg.jpg?imwidth=292'
  },
  {
    id: 9,
    nome: 'Cueca',
    preco: 19.9,
    quant: 1,
    img: 'https://cf.shopee.com.br/file/4d10a84d16bd3f594cb5bf5fe33fef4d'
  }
])

const carrinho = ref({
  items: [],
  valorTotal: 0
})

function adicionar(pos) {
  produtos.value[pos].quant++
}

function remover(pos) {
  if (produtos.value[pos].quant > 1) {
    produtos.value[pos].quant--
  }
}

function adcCarrinho(i) {
  const produto = produtos.value[i]
  carrinho.value.items.push({ ...produto, total: produto.preco * produto.quant })
  carrinho.value.valorTotal += produto.preco * produto.quant
}

function removerDoCarrinho(i) {
  carrinho.value.items.splice(i, 1)
  totalCarrinho()
}

function limparCarrinho() {
  carrinho.value.items = []
  totalCarrinho()
}


  function totalCarrinho(){
    carrinho.value.valorTotal = 0
    for (let item of carrinho.value.items){
      carrinho.value.valorTotal += item.quant * item.preco
    }
  }

</script>

<template>
  <header>
    <nav>
      <img
        class="logo"
        src="https://logodetimes.com/times/corinthians/logo-do-corinthians-4096.png"
      />
      <h1 class="titulo">Loja do Timão</h1>
      <ul class="menu">
        <li><a href="">Home</a></li>
        <li><a href="">Novidades</a></li>
        <li><a href="">Contato</a></li>
        <li><button @click="mostrarDiv = !mostrarDiv" class="botaoCarrinho">Carrinho</button></li>
      </ul>
    </nav>
  </header>
  <div class="flex">
    <div class="produtos" id="container">
      <div v-for="(produto, i) in produtos" :key="i" class="card-produtos">
        <h2>{{ produto.nome }}</h2>
        <img :src="produto.img" />
        <p>R$ {{ produto.preco.toFixed(2).replace('.', ',') }}</p>
        <p>Quantidade: {{ produto.quant }}</p>
        <div>
          <button @click="adcCarrinho(i)">Adicionar ao carrinho</button>
        </div>
      </div>
    </div>
    <div class="carrinho" v-if="(mostrarDiv = mostrarDiv)">
      <h1>Seu carrinho</h1>
      <ul>
        <li v-for="(item, i) in carrinho.items" :key="item.id">
          Quantidade: {{ item.quant }}
          <p>Produto: {{ item.nome }}: R${{ item.preco }}</p>
          <button @click="adicionar(i)">+</button>
          <button @click="remover(i)">-</button>
          <button @click="removerDoCarrinho(i)">remover</button>
        </li>
      </ul>
      R${{ carrinho.valorTotal.toFixed(2) }}
      <button @click="limparCarrinho()">Limpar carrinho</button>
    </div>
  </div>
</template>

<style scoped>
.flex {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
}
.card-produtos {
  width: 70%;
  margin: 10px;
  width: 300px;
  height: 350px;
  border: 0;
  border-radius: 10px;
  box-shadow: rgba(50, 50, 93, 0.25) 3px 2px 5px 3px, rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
  display: flex;
  flex-direction: column;
  align-items: center;
  transition: all 0.3s;
}

.card-produtos:hover {
  transition: 0.3s;
  transform: scale(1.1);
}
.card-produtos > img {
  width: 70%;
}

.produtos {
  margin: 100px 60px 100px 60px;
  display: grid;
  grid-template-columns: repeat(4, 10fr);
  grid-auto-rows: 400px;
}

#container {
  display: grid;
  grid: repeat(3, 400px) / auto-flow 350px;
}

button {
  border: 0;
  margin: 2px 2px;
  border-radius: 5px;
  border-color: rgb(245, 245, 245);
  color: black;
  background-color: rgb(224, 223, 223);
  font-weight: bold;
  font-size: 1em;
}

button:hover {
  background-color: rgb(78, 78, 78);
  color: white;
}

h2,
p {
  margin: 5px;
}

nav {
  display: flex;
  justify-content: space-between;
  font-size: 1.2rem;
  padding: 10px;
}

nav li {
  float: left;
}

nav li a {
  display: block;
  font-family: 'Times New Roman', Times, serif;
  color: black;
  padding: 16px 16px;
  text-decoration: none;
}

nav > ul {
  list-style-type: none;
  padding: 0;
  overflow: hidden;
}

li {
  list-style-type: none;
}
.logo {
  margin: 0;
  padding: 0;
  width: 6%;
  height: 5%;
}
.titulo {
  margin-right: 50%;
  font-size: 2rem;
  font-family: 'Times New Roman', Times, serif;
}

.botaoCarrinho {
  display: block;
  font-family: 'Times New Roman', Times, serif;
  color: black;
  padding: 16px 16px;
  text-decoration: none;
}
.carrinho {
  margin: 10px 10px;
  padding: 10px 10px;
  max-width: 250px;
  font-style: normal;
  align-content: end;
}
</style>
