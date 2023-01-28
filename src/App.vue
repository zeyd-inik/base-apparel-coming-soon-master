<script setup>
import { ref } from 'vue';
const error = ref(false);
const input = ref('');
const success = ref(false);
const handleSubmit = () => {
    const emailRegex =
        /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    if (!emailRegex.test(input.value)) {
        error.value = true;
    } else {
        error.value = false;
        input.value = '';
        success.value = true;
        setTimeout(() => {
            success.value = false;
        }, 2500);
    }
};
const clearError = () => {
    const emailRegex =
        /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    if (emailRegex.test(input.value)) {
        error.value = false;
    }
};
</script>

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
                <form @submit.prevent="handleSubmit" class="form">
                    <input
                        :class="{ red: error }"
                        v-model="input"
                        class="text_input"
                        type="text"
                        placeholder="Email Adress"
                        @input="clearError"
                    />
                    <button class="btn" type="submit">
                        <img src="./assets/images/icon-arrow.svg" />
                    </button>
                    <div v-if="error" class="error_icon_container">
                        <img src="./assets/images/icon-error.svg" alt="error icon" />
                    </div>
                    <p class="error_message_container" v-if="error">Please provide a valid email</p>

                    <Transition name="success">
                        <p class="error_message_container success" v-if="success">
                            The mail has been sent successfully
                        </p>
                    </Transition>
                </form>
            </div>
        </section>
        <section class="img_desktop_container">
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

.success-enter-active,
.success-leave-active {
    transition: opacity 0.5s;
}
.success-enter-from,
.success-leave-to {
    opacity: 0;
}

//Global Styles
* {
    font-family: 'Josefin Sans', sans-serif;
    font-size: 16px;
    box-sizing: border-box;
}
.app {
    width: 100vw;
    background-image: linear-gradient(135deg, $Linear_from_1, $Linear_to_1);
    overflow: hidden;
    @media (min-width: 768px) {
        display: grid;
        grid-template-columns: 50vw 50vw;
        overflow: hidden;
    }

    .main_text_container {
        overflow: hidden;
        display: grid;
        grid-template-rows: 60px 250px auto;
        width: 100vw;
        @media (min-width: 768px) {
            grid-template-rows: 200px auto;
            width: 50vw;
            height: 100vh;
            max-width: 500px;
            margin-right: auto;
            margin-left: auto;
        }

        .header {
            display: flex;
            align-items: center;
            justify-content: flex-start;
            margin: 0 2rem;
            @media (min-width: 768px) {
                margin-right: auto;
                padding-top: 4rem;
                padding-bottom: 4rem;
            }
            img {
                height: 1.5rem;
            }
        }
        .img_mobile_container {
            margin-bottom: 2rem;
            overflow: hidden;
            width: auto;
            max-height: 300px;
            @media (min-width: 768px) {
                display: none;
            }

            img {
                object-fit: cover;
                object-position: top left;
                width: 100%;
                height: 100%;
                display: inline-block;
            }
        }
        .text_info_container {
            padding: 0 0.3rem;
            max-width: 500px;
            margin: 0 auto;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            @media (max-width: 320px) {
                padding-left: 0;
                padding-right: 0;
            }
            @media (min-width: 768px) {
                transform: translateY(-50px);
            }

            .title_container {
                display: flex;
                flex-direction: column;
                align-items: center;
                justify-content: center;

                h1 {
                    font-size: 2.4rem;
                    margin: 0;
                    letter-spacing: 5px;
                    color: $Dark-Grayish-Red;
                    @media (min-width: 414px) {
                        font-size: 2.3rem;
                    }
                    @media (min-width: 768px) {
                        font-size: 3rem;
                    }
                }
                h1.pink_color_text {
                    color: $Desaturated-Red;
                    font-weight: 300;
                }
            }
            .description {
                color: $Desaturated-Red;
                line-height: 1.4;
                text-align: center;
                font-size: 16px;
                padding: 1rem 0;
                @media (min-width: 414px) {
                    font-size: 16px;
                    padding: 1rem 0;
                }
                @media (min-width: 768px) {
                    font-size: 17px;
                    padding-top: 2.3rem;
                    padding-bottom: 2.3rem;
                }
            }
            .form {
                width: 100%;
                display: flex;
                align-items: center;
                justify-content: center;
                position: relative;
                margin: 0 auto 2rem auto;
                @media (max-width: 375px) {
                    transform: scaleX(0.95);
                }
                .text_input {
                    padding: 0.7rem 1rem;
                    width: 100%;
                    border: 1px solid $Desaturated-Red;
                    border-radius: 50px;
                    @media (max-width: 500px) {
                        font-size: 14px;
                    }
                    &:focus {
                        outline: none;
                        color: $Dark-Grayish-Red;
                        font-size: 16px;
                    }
                    &::placeholder {
                        opacity: 0.5;
                    }
                    @media (max-width: 375px) {
                        width: 90%;
                    }
                }

                .text_input.red {
                    border: 2px solid $Soft-Red;
                }
                /* update active state clicking effect */
                .btn {
                    display: inline-block;
                    position: absolute;
                    right: 0;
                    top: 0;
                    height: 100%;
                    width: 70px;
                    border-radius: 50px;
                    border: none;
                    display: flex;
                    align-items: center;
                    justify-content: center;
                    background-image: linear-gradient(135deg, $Linear_from_2, $Linear_to_2);
                    transition: all ease 0.3s;

                    &:hover {
                        cursor: pointer;
                        box-shadow: $Linear_from_2 0px 11px 20px 4px;
                    }
                    img {
                        transform: translateX(20%);
                    }
                }
                .error_icon_container {
                    position: absolute;
                    top: 9px;
                    right: 80px;
                }
            }
            .error_message_container {
                position: absolute;
                bottom: -24px;
                left: 5px;
                font-size: 15px;
                color: $Soft-Red;
                padding: 0 1rem;
                width: 320px;
                margin: 0 auto 0 0;
            }
            .error_message_container.success {
                color: green;
            }
        }
    }
    .img_desktop_container {
        height: 100vh;
        img {
            object-fit: cover;
            object-position: top center;
            width: 100%;
            height: 100%;
            display: inline-block;
        }

        @media (max-width: 767px) {
            display: none;
        }
    }
}
</style>
