<template>
<footer>
    <div class="container">
        <p>
            <strong>AvisaLoto</strong> Copyright © {{ currentYear }}. <br />
            Todos os direitos reservados.
        </p>
    </div>
</footer>
</template>

<script>
export default {
    data() {
        return {
            currentYear: new Date().getFullYear(),
        }
    }
}
</script>

<style scoped>
footer {
    width: 100%;
    padding: 40px 0;
    background: #DDE9FF;
    color: #515C71;
    font-family: 'Raleway', sans-serif;
    font-size: 15px;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}
footer div p { margin: 0; }
footer div p strong {
    font-weight: 600;
}
</style>