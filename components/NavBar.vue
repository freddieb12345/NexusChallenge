<template>
    <section class="container">
        <nav class="navbar">Navbar</nav>
    </section>
</template>

<style lang="scss" scoped>
@import '~/assets/scss/variables.scss';

.navbar {
    height: $navbar-height-large;
    background-color: white;
    border: 1px black solid;
    text-align: center;

    @media (max-width: 349px) {
        height: $navbar-height-mobile;
    }

    @media (min-width: 350px) and (max-width: 768px) {
        height: $navbar-height-tablet;
    }
}
</style>
