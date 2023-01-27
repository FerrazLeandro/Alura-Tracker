<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="Logo Ferraz Task">
        </h1>
        <Botao @click="alterarTema" :icone=tema texto="" />
        <nav class="panel mt-5">
            <ul>
                <li>
                    <router-link to="/" class="link">
                        <i class="fas fa-tasks">
                            Tarefas
                        </i>
                    </router-link>
                </li>
                <li>
                    <router-link to="/projetos" class="link">
                        <i class="fas fa-project-diagram">
                            Projetos
                        </i>
                    </router-link>
                </li>
            </ul>
        </nav>
    </header>
</template>


<script lang="ts">
import { defineComponent } from 'vue';
import Botao from './Botao.vue';

export default defineComponent({
    name: "BarraLateral",
    emits: ["aoTemaAlterado"],
    data() {
        return {
            modoEscuroAtivo: false
        };
    },
    computed: {
        tema() {
            if (this.modoEscuroAtivo) {
                return "fa-sharp fa-solid fa-sun";
            }
            else {
                return "fa-sharp fa-solid fa-moon";
            }
        }
    },
    methods: {
        alterarTema() {
            this.modoEscuroAtivo = !this.modoEscuroAtivo;
            this.$emit("aoTemaAlterado", this.modoEscuroAtivo);
        }
    },
    components: { Botao }
})
</script>


<style scoped>
/* Todo o estilo do componente */
header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;
}

@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}

.panel li {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin: 8px 0px;
    padding: 4px;
}

.link {
    color: #FFFF;
}

.link:hover{
    color: #FAF0CA;
}

.link.router-link-active {
    color: #FAF0CA;
}

</style>