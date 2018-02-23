<template>

    <div class="app">
        <div class="app__container">
            <div class="app__inner">
                <div class="app__info app__side">
                    <div class="app__title"><h1>Vue<br/>Spinner<br/>Component</h1></div>
                    <div class="app__likes">
                        <a class="github-button" href="https://github.com/sergeyloysha/vue-spinner-component" data-icon="octicon-star" data-show-count="true" aria-label="Star sergeyloysha/vue-spinner-component on GitHub">Star</a>
                    </div>
                    <div class="app__sources">
                        <a href="https://github.com/sergeyloysha/vue-spinner-component/archive/master.zip" class="app__btn">Download</a>
                        <a href="https://github.com/sergeyloysha/vue-spinner-component" class="app__btn app__btn_transparent" target="_blank">Source on Github</a>
                    </div>

                    <div class="app__copy">
                        &copy; 2018 Sergey Loysha / <a href="http://loysha.com" target="_blank">loysha.com</a>
                    </div>
                </div>
                <div class="app__preview app__side">
                    <div class="app__spinner">
                        <spinner :status="spinner.status" :color="spinner.color" :size="spinner.size" :depth="spinner.depth" :rotation="spinner.rotation" :speed="spinner.speed"></spinner>
                    </div>
                    <div class="app__controls">
                        <div class="sl-controls__item">
                            <label for="size">Status</label>
                            <button class="sl-controls__item-ctrl" v-model="spinner.status" @click="spinner.status = !spinner.status">{{ statusMessage }}</button>
                        </div>

                        <div class="sl-controls__item">
                            <label for="size">Size</label>
                            <input class="sl-controls__item-ctrl" type="range" min="30" max="150" step="5" v-model="spinner.size" id="size">
                        </div>

                        <div class="sl-controls__item">
                            <label for="depth">Depth</label>
                            <input class="sl-controls__item-ctrl" type="range" min="1" max="10" step="1" v-model="spinner.depth" id="depth">
                        </div>

                        <div class="sl-controls__item">
                            <label for="color">Color</label>
                            <input class="sl-controls__item-ctrl" type="text"  v-model="spinner.color" id="color" :style="{ color: spinner.color}">
                        </div>

                        <div class="sl-controls__item">
                            <label for="clockwise">Rotation</label>
                            <button class="sl-controls__item-ctrl" v-model="spinner.rotation" @click="spinner.rotation = !spinner.rotation">{{ rotationMessage }}</button>
                        </div>

                        <div class="sl-controls__item">
                            <label for="speed">Speed</label>
                            <input class="sl-controls__item-ctrl __rtl" type="range" min="0.5" max="2" step="0.01" v-model="spinner.speed" id="speed">
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

</template>

<script>

    import Spinner from './Spinner.vue'

    export default {
        components: {
            Spinner
        },

        data() {
            return {
                spinner: {
                    size: 50,
                    status: true,
                    color: '#4fc08d',
                    depth: 3,
                    rotation: true,
                    speed: 0.8,
                }
            }
        },

        computed: {
            statusMessage() {
                return this.spinner.status ? 'Active' : 'Inactive';
            },

            rotationMessage() {
                return this.spinner.rotation ? 'Forward' : 'Backward';
            }
        }
    }

</script>

<style lang="scss">

    $color-indigo: #5528ff;
    $color-green: #4fc08d;
    $color-black: #000000;
    $color-default: #3c4858;
    $color-white: #ffffff;
    $color-bg: #eff2f7;

    $sm: 768px;

    * {
        -webkit-box-sizing: border-box;
        -moz-box-sizing: border-box;
        box-sizing: border-box;
    }

    html {
        font-size: 62.5%;
        background: #eff2f7;
        text-rendering: optimizeLegibility;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
    }

    body {
        margin: 0;
        font: 400 1.4rem/1.4 'Roboto', 'Helvetica Neue', Arial, sans-serif;
        color: $color-default;
    }

    a {
        transition: color .25s;
    }

    .app {
        padding: 1rem 0;

        @media screen and (min-width: $sm) {
            padding: 5rem 0;
        }

        &__container {
            width: 100%;
            max-width: 96rem;
            margin: 0 auto;
            padding: 0 1rem;
        }

        &__inner {
            display: flex;
            flex-direction: column;

            @media screen and (min-width: $sm) {
                flex-direction: row;
                align-items: stretch;
            }
        }

        &__side {
            flex-shrink: 0;
            padding: 5rem;

            @media screen and (min-width: $sm) {
                width: 50%;
            }
        }

        &__preview {
            border-radius: .4rem;
            background: #fff;
        }

        &__title {
            h1 {
                font-size: 5.2rem;
                font-weight: 900;
                line-height: 1.3;
                margin: 0 0 3rem 0;
                color: $color-green;
            }
        }

        &__likes {
            margin-bottom: 3rem;
        }

        &__spinner {
            display: flex;
            align-items: center;
            justify-content: center;
            height: 15rem;
            margin-bottom: 5rem;
        }

        &__btn {
            display: inline-block;
            padding: 1rem 2rem;
            background: $color-green;
            color: #fff;
            border-radius: .2rem;

            margin: 0 1rem 0 0;

            text-decoration: none;
            outline: 0;
            transition: opacity .15s linear;
            border: 1px solid $color-green;

            &:hover {
                opacity: .8;
            }

            &_transparent {
                background: transparent;
                color: $color-default;
                border-color: rgba($color-default, .1);
            }
        }

        &__copy {
            display: none;

            @media screen and (min-width: $sm) {
                display: block;
                padding-top: 5rem;
                color: rgba($color-black, .2);

                a {
                    color: $color-green;
                    text-decoration: none;
                }
            }
        }

        &__controls {
            margin: 0 -5rem -5rem -5rem;
            padding: 5rem;
            border-radius: 0 0 .4rem .4rem;
        }
    }

    .sl {
        &-controls {

            &__item {
                margin-bottom: 2rem;
                display: flex;
                align-items: center;

                &:last-child {
                    margin-bottom: 0;
                }

                label {
                    font-weight: 300;
                    font-size: 1.8rem;
                    width: 50%;
                    min-width: 10rem;
                    margin-right: 1rem;
                    padding-right: 1rem;
                    text-align: right;

                    &:after {
                        content: ':';
                    }
                }

                button {
                    border: 0;
                    background: $color-bg;
                    color: $color-green;
                    font-weight: 600;
                    padding: 1rem;
                    border-radius: .4rem;
                    outline: none;
                    transition: background .25s;
                    cursor: pointer;
                }

                input {
                    outline: 0;
                }

                input[type="range"].__rtl {
                    direction: rtl
                }

                input[type="text"] {
                    font-weight: 600;
                    border: 0;
                    padding: 1rem;
                    border-radius: .4rem;
                    background: $color-bg;
                }

                input[type=range] {
                    -webkit-appearance: none;
                    width: 100%;
                    background: $color-bg;
                    max-width: 14.5rem;
                    height: 1.5rem;
                    border-radius: 1rem;
                }

                input[type=range]::-webkit-slider-thumb {
                    -webkit-appearance: none;
                    width: 1.5rem;
                    height: 1.5rem;
                    background: $color-green;
                    border-radius: 100%;
                }

                input[type=range]::-moz-range-thumb {
                    -webkit-appearance: none;
                    width: 1.5rem;
                    height: 1.5rem;
                    background: $color-green;
                    border-radius: 100%;
                    border: 0;
                }

                input[type=range]:focus {
                    outline: none;
                }

                input[type=range]::-ms-track {
                    width: 100%;
                    cursor: pointer;

                    border-color: transparent;
                    color: transparent;
                }

                input[type=range]::-moz-range-track  {
                    -webkit-appearance: none;
                    width: 100%;
                    background: $color-bg;
                    max-width: 14.5rem;
                    height: 1.5rem;
                    border-radius: 1rem;
                    outline: none;
                }

            }
        }
    }
</style>
