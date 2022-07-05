<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      nova_categoria: "",
      categorias: [
        { id: "f12bc7ce-5ca7-4cbf-ac6e-be3e59cb2862", categoria: "Romance" },
        { id: "b880659d-5d33-4607-ae19-8a22a738b509", categoria: "Suspense" },
        { id: "0f97fea6-72ac-4ee0-bf1b-92516d3417e1", categoria: "Ficção" },
        { id: "25c441be-e90a-4847-98a7-0d888e4c981f", categoria: "Drama" },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.nova_categoria !== "") {
        const novo_id = uuid();
        this.categorias.push({
          id: novo_id,
          categoria: this.nova_categoria,
        });
        this.nova_categoria = "";
      }
    },
    excluir(categoria) {
      const indice = this.categorias.indexOf(categoria);
      this.categorias.splice(indice, 1);
    },
    alerta() {
      alert("Ok!");
    },
  },
};
</script>

<template>
  <div class="position-absolute top-50 start-50 translate-middle">
    <div class="formulario">
      <div class="title">
        <h2>Gerencimento de Categorias</h2>
      </div>
      <div class="form-input container d-flex">
        <select class="form-select" v-model="nova_categoria">
            <option value="" class="col form-control d-flex" disabled>Categoria</option>
            <option value="Categoria 1">Categoria 1</option>
            <option value="Categoria 2">Categoria 2</option>
            <option value="Categoria 3">Categoria 3</option>
            <option value="Categoria 4">Categoria 4</option>
            <option value="Categoria 5">Categoria 5</option>
          </select>

        <button class="btn btn_save" @click="salvar">Salvar</button>
      </div>
    </div>

    <div class="list-items">
      <table>
        <thead>
          <tr>
            <td>ID</td>
            <td>Categorias</td>
            <td>Ações</td>
          </tr>
        </thead>
        <tbody>
          <tr v-for="categoria in categorias" :key="categoria.id">
            <td>{{ categoria.id }}</td>
            <td>{{ categoria.categoria }}</td>

             <td class="button-group d-flex salvar_editar">
              <button class="btn btn-primary" @click="alerta(livro)">Editar</button>
              <button class="btn btn-danger" @click="excluir(livro)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style></style>
