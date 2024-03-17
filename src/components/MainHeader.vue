<template>
<div class="container py-3" id="top">
    <header>
        <input type="checkbox" id="checkBtn">
        <label for="checkBtn" class="toggler-nav">
            <span></span>
            <span></span>
            <span></span>
        </label>
        <nav>
            <div class="nav-container">
                <router-link to="/" @click="unChecked">Home</router-link>
                <router-link to="/" @click="unChecked">Mega-Sena</router-link>
                <router-link to="/" @click="unChecked">Dupla Sena</router-link>
                <router-link to="/" @click="unChecked">Lotofácil</router-link>
                <router-link to="/" @click="unChecked">Quina</router-link>
                <router-link to="/" @click="unChecked">Timemania</router-link>
                <router-link to="/" @click="unChecked">Lotomania</router-link>
                <router-link to="/" @click="unChecked">Dia de Sorte</router-link>
                <router-link to="/" @click="unChecked">Super Sete</router-link>
                <router-link to="/" @click="unChecked">Mais Milionária</router-link>
            </div>
        </nav>
        <div class="search">
            <input type="search" name="" id="">
            <button class="submit"><i class="bi bi-search"></i></button>
        </div>
        <router-link to="/">
            <img src="@/assets/logo.png" alt="">
        </router-link>
    </header>
</div>
</template>

<script>
export default {
    methods: {
        unChecked() {
            document.getElementById('checkBtn').checked = false;
        },
    }
}
</script>

<style scoped>
@media screen and (max-width: 800px) {
    #top { position: fixed; top: 0; left: 0; background: #FFF; }
}

header {
    display: flex;
    width: 100%;
    justify-content: space-between;
    align-items: center;
}

.toggler-nav {
    width: 30px;
    height: 30px;
    display: table;
    position: relative;
    z-index: 100;
    cursor: pointer;
    transition: .3s ease all;
}

.toggler-nav span {
    width: 80%;
    height: 2px;
    background: #372B6B;
    display: table;
    margin-bottom: 7px;
    transition: .3s ease all;
}

.toggler-nav span:nth-child(2) {
    width: 100%;
}

.toggler-nav span:nth-child(3) {
    margin-bottom: 0;
}

#checkBtn {
    display: none;
}

#checkBtn:checked ~ nav {
    left: 0;
}

#checkBtn:checked ~ .toggler-nav span:nth-child(2) {
    transform: translateX(-10px);
    opacity: 0;
}

#checkBtn:checked ~ .toggler-nav span:nth-child(1) {
    transform: translatey(9px) rotate(45deg);
}

#checkBtn:checked ~ .toggler-nav span:nth-child(3) {
    transform: translatey(-9px) rotate(-45deg);
}

nav {
    width: 100%;
    height: 100vh;
    position: fixed;
    top: 73px;
    left: -100%;
    background: #372B6B;
    color: #FFF;
    transition: .3s ease all;
}

nav div {
    display: flex;
    flex-direction: column;
    gap: 12px;
    padding: 30px 0;
}

nav div a {
    font-size: 1.2rem;
    color: #FFF;
    text-decoration: none;
    transition: .3s ease all;
    padding-left: 30px;
    border-left: 3px solid #372B6B;
}

nav div a:hover {
    color: #FFBC0F;
    font-weight: 600;
    transform: translateX(10px);
    border-left: 3px solid #FFBC0F;
}

.search {
    border: 1px solid #EAEAEA;
    border-radius: 100px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 250px;
}

.search input {
    border: none;
    outline: none;
    background: none;
    width: 90%;
    padding: 5px 20px;
    box-sizing: border-box;
    font-size: 17px;
    color: #372B6B;
    display: table;
}

.search button {
    background: none;
    border: none;
    color: #c6c6c6;
    margin-right: 7px;
}
</style>