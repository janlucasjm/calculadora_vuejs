<script setup>
    const props = defineProps(['primeiroNumero', 'segundoNumero', 'selecionaLista', 'getOperacoes'])
</script>

<template>
    <form class="py-5 ps-4 bg-body-secondary rounded-2">
        <div class="row">
            <div class="col-md-2">
                <input @keyup="props.primeiroNumero" class="form-control" type="number" placeholder="Digite o primeiro número">
            </div>
            <div class="col-md-2">
                <input @keyup="props.segundoNumero" type="number" class="form-control" placeholder="Digite o segundo número">
            </div>
            <div class="col-md-3">
                <select @change="props.selecionaLista" class="form-control">
                    <option value="selecione" disabled selected>Selecione a operação:</option>
                    <option value="soma">Soma</option>
                    <option value="subtracao">Subtração</option>
                    <option value="multiplicacao">Multiplicação</option>
                    <option value="divisao">Divisão</option>
                </select>
            </div>
            <div class="col-md-4 d-flex align-items-center fs-4 fw-bold">
                <span>Resultado: {{ props.getOperacoes }}</span>
            </div>
        </div>
    </form>
</template>