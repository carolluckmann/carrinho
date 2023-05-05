<script setup>
  import { ref } from 'vue';

  const produtos = [
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.90
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90
    },
    {
        id: 4,
        nome: 'Sapato',
        preco: 199.90
    },
    {
        id: 5,
        nome: 'Boné',
        preco: 29.90
    },
    {
        id: 6,
        nome: 'Óculos',
        preco: 99.90
    },
    {
        id: 7,
        nome: 'Relógio',
        preco: 299.90
    },
    {
        id: 8,
        nome: 'Bermuda',
        preco: 79.90
    },
    {
        id: 9,
        nome: 'Cueca',
        preco: 19.90
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
            <p> R$ {{ produto.preco.toFixed(2).replace('.',',') }}</p>
            <p> Quantidade: </p>
        </div>
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
    #container{
        display: grid;
        grid: repeat(2, 200px) / auto-flow 350px;

    }
</style>
