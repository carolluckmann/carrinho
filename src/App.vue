<script setup>
  import { ref } from 'vue';

  const mostrarDiv = ref(false)


  const produtos = [
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.90,
        quant: 1,
        img: 'https://d2p7wtszppk2p4.cloudfront.net/Custom/Content/Products/55/19/55191_camisa-1-corinthians-jogador-pr-7852-cv7855100_m2_637818328664576428.jpg'
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90,
        quant: 1,
        img: 'https://static.shoptimao.com.br/produtos/calca-moletom-corinthians-juvenil-phillip/06/D65-2254-006/D65-2254-006_zoom1.jpg?ts=1564482873&ims=544x'
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90,
        quant: 1,
        img: 'https://images-americanas.b2w.io/produtos/1517617581/imagens/meiao-infantil-corinthians-preto-oficial/1517617599_1_large.jpg'
    },
    {
        id: 4,
        nome: 'Sapato',
        preco: 199.90,
        quant: 1,
        img: 'https://static3.tcdn.com.br/img/img_prod/311840/tenis_corinthians_street_preto_e_branco_86854_1_20201130180734.jpg'
    },
    {
        id: 5,
        nome: 'Boné',
        preco: 29.90,
        quant: 1,
        img: 'https://static.netshoes.com.br/produtos/bone-nike-corinthians-aba-curva/26/D12-8176-026/D12-8176-026_zoom1.jpg?ts=1603734784&ims=544x'
    },
    {
        id: 6,
        nome: 'Óculos',
        preco: 99.90,
        quant: 1,
        img: 'https://sportscenter.loja2.com.br/img/ba01929694145290234d80ee63a933a4.png'
    },
    {
        id: 7,
        nome: 'Relógio',
        preco: 299.90,
        quant: 1,
        img: 'https://static.shoptimao.com.br/produtos/relogio-corinthians-technos-analogico-masculino/06/F61-1223-006/F61-1223-006_zoom1.jpg?ts=1603733030'
    },
    {
        id: 8,
        nome: 'Bermuda',
        preco: 79.90,
        quant: 1,
        img: 'https://imgs.casasbahia.com.br/1544057339/1xg.jpg?imwidth=292'
    },
    {
        id: 9,
        nome: 'Cueca',
        preco: 19.90,
        quant: 1,
        img: 'https://cf.shopee.com.br/file/4d10a84d16bd3f594cb5bf5fe33fef4d'
    }
]

const carrinho = [
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.90,
        quantidade: 1,
        valorTotal: 49.90
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90,
        quantidade: 2,
        valorTotal: 199.80
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90,
        quantidade: 4,
        valorTotal: 39.60
    }
    ,
    {total: 288.30}
]
</script>

<template>
    <div id="container">
        <div v-for="(produto, i) in produtos" :key="i" class="card-produtos">
            <h2>{{ produto.nome }}</h2>
            <img :src="produto.img" >
            <p> R$ {{ produto.preco.toFixed(2).replace('.',',') }}</p>
            <p> Quantidade: {{ produto.quant }} </p>
            <button>+</button>
            <button>-</button>
            <button>Adicionar ao carrinho</button>
        </div>
    </div>
    <div class="mostraDiv" v-if="mostrarDiv">
        <h1>Seu carrinho</h1>

    </div>
</template>

<style scoped>
    .card-produtos{
        margin-left: 15px;
        width: 300px;
        height: 200px;
        border: 0;
        border-radius: 10px;
        box-shadow: rgba(50, 50, 93, 0.25) 3px 2px 5px 3px, rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
    }
   
    .card-produtos > img{
        width: 30%;
    }

    #container{
        display: grid;
        grid: repeat(2, 200px) / auto-flow 350px;
    }

    h2, p {
        margin: 5px;
    }
    
</style>
