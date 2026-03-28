<script setup>
import { ref, onMounted } from 'vue';

const recados = ref([]);
const autor = ref('');
const mensagem = ref('');

async function buscarRecados() {
    const response = await fetch('http://localhost:4000/recados');
    const dados = await response.json();
    recados.value = dados;
}

async function adicionarRecado() {
    const novoRecado = {
        autor: autor.value,
        mensagem: mensagem.value
    };

    const response = await fetch('http://localhost:4000/recados', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(novoRecado)
    });

    if (response.ok) {
        await buscarRecados();
        autor.value = '';
        mensagem.value = '';
    } else {
        console.error('Erro ao adicionar recado');
    }
}

async function excluirRecado(id) {
    const response = await fetch(`http://localhost:4000/recados/${id}`, {
        method: 'DELETE'
    });

    if (response.ok) {
        await buscarRecados();
    } else {
        console.error('Erro ao excluir recado');
    }
}

onMounted(async () => {
    await buscarRecados();
})

</script>

<template>
    <div class="container">

        <div class="titulo">
            <h1>Mural de Recados</h1>
        </div>

        <div class="recados">
            <div v-for="recado in recados" :key="recado.id">
                <h2>{{ recado.autor }}</h2>
                <p>{{ recado.mensagem }}</p>
                <button @click="excluirRecado(recado.id)">Excluir</button>

            </div>
        </div>

        <div class="formulario">
            <form @submit.prevent="adicionarRecado">
                <input v-model="autor" placeholder="Autor" />
                <input v-model="mensagem" placeholder="Mensagem" />
                <button type="submit">Adicionar</button>
            </form>
        </div>
    </div>
</template>

<style scoped>
.container {
    max-width: 600px;
    margin: 40px auto;
    padding: 20px;
    background: #f9fafb;
    border-radius: 12px;
    font-family: Arial, sans-serif;
}

.titulo {
    text-align: center;
    margin-bottom: 20px;
}

.titulo h1 {
    color: #1f2937;
}

.formulario form {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
}

.formulario input {
    flex: 1;
    padding: 10px;
    border: 1px solid #d1d5db;
    border-radius: 8px;
    outline: none;
}

.formulario input:focus {
    border-color: #3b82f6;
}

.formulario button {
    padding: 10px 16px;
    background: #3b82f6;
    color: white;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: 0.2s;
}

.formulario button:hover {
    background: #2563eb;
}

.recados {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 20px; 
}

.recados>div {
    background: white;
    padding: 15px;
    border-radius: 10px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
    position: relative;
}

.recados h2 {
    margin: 0;
    font-size: 16px;
    color: #111827;
}

.recados p {
    margin: 5px 0 0;
    color: #4b5563;
}

.recados button {
  position: absolute;
  top: 50%;
  right: 10px;
  transform: translateY(-50%);
  
  background: #ef4444;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 6px;
  cursor: pointer;
  transition: 0.2s;
}

.recados button:hover {
    background: #dc2626;
}
</style>
