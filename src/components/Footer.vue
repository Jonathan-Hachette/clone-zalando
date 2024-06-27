<!-- eslint-disable vue/multi-word-component-names -->

<template>

    <footer>
       <p>Made by </p><a href="https://github.com/Jonathan-Hachette"> Jonathan Hachette</a>
    </footer>

</template>

<style scoped>

    footer{
        display: flex;
        justify-content:  center;
        align-items: center;
        height: var(--footer-height);
    }

    a {
        padding-left: 5px;
        color: var(--main-orange);
        font-weight: bold;
        text-decoration: none;
    }
</style>