<template>
    <div>
        <h1>Hola mundo</h1>
        <h2>{{ texto }}</h2>
    </div>
</template>
<script>
export default {
    name: 'micomponente',
    data() {
        return {
            texto: "mundo bonito"
        }
    }
}
</script>




