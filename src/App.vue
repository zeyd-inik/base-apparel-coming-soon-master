<script setup></script>

<template>
    <div class="app">
        <section class="main_text_container">
            <header class="header">
                <img src="./assets/images/logo.svg" alt="logo" />
            </header>
            <div class="img_mobile_container">
                <img src="./assets/images/hero-mobile.jpg" alt="girl" />
            </div>
            <div class="text_info_container">
                <div class="title_container">
                    <h1 class="pink_color_text">WE'RE</h1>
                    <h1>COMING</h1>
                    <h1>SOON</h1>
                </div>
                <p class="description">
                    Hello fellow shoppers! We're currently building our new fashion store. Add your email below to stay
                    up-to-date with announcements and our launch deals
                </p>
                <form class="form">
                    <input class="text_input" type="text" />
                    <button type="submit">
                        <img src="./assets/images/icon-arrow.svg" />
                    </button>
                </form>
            </div>
        </section>
        <section class="img_desktop_container">
            <!-- add css as display none -->
            <img src="./assets/images/hero-desktop.jpg" alt="girl" />
        </section>
    </div>
</template>

<style lang="scss" scoped>
//custon font
@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@300;400;600&display=swap');

//colors
$Desaturated-Red: hsl(0, 36%, 70%);
$Soft-Red: hsl(0, 93%, 68%);
$Dark-Grayish-Red: hsl(0, 6%, 24%);

// gradients - 135deg
$Linear_from_1: hsl(0, 0%, 100%);
$Linear_to_1: hsl(0, 100%, 98%);
$Linear_from_2: hsl(0, 80%, 86%);
$Linear_to_2: hsl(0, 74%, 74%);

//Global Styles
* {
    font-family: 'Josefin Sans', sans-serif;
    font-size: 16px;
}
</style>
