<script setup lang="ts">
import SerieList from '@/components/series/SerieList.vue'
import SerieSave from '@/components/series/SerieSave.vue'
import Button from 'primevue/button'
import { ref } from 'vue'

const mostrarDialog = ref<boolean>(false)
const serieListRef = ref<typeof SerieList | null>(null)
const serieEdit = ref<any>(null)

function hableCreate() {
    serieEdit.value = null
    mostrarDialog.value = true
}

function handleEdit(serie: any) {
    serieEdit.value = serie
    mostrarDialog.value = true
}

function handleCloseDialog() {
    mostrarDialog.value = false
}

function handleGuardar() {
    serieListRef.value?.obtenerLista()
}
</script>

<template>
    <div>
        <h1>Series</h1>
        <Button label="Crear Nuevo" icon="pi pi-plus" @click="hableCreate" />
        <SerieList ref="serieListRef" @edit="handleEdit" />
        <SerieSave :mostrar="mostrarDialog" :serie="serieEdit" :modoEdicion="!!serieEdit" @guardar="handleGuardar"
            @close="handleCloseDialog" />
    </div>
</template>

<style scoped></style>