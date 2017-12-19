<template>

    <div class="sl">
        <div class="sl-container">
            <div class="sl-content">
                <h1 class="sl-title">Vue Spinner Component</h1>
                <h3 class="sl-subtitle">vue-spinner-component</h3>
                <div class="sl-socials">
                    <a class="github-button" href="https://github.com/sergeyloysha/vue-spinner-component" data-icon="octicon-star" data-show-count="true" aria-label="Star sergeyloysha/vue-spinner-component on GitHub">Star</a>
                </div>

                <div class="sl-btns">
                    <a href="https://github.com/sergeyloysha/vue-spinner-component" class="sl-btn" target="_blank">Source on Github</a>
                    <a href="https://github.com/sergeyloysha/vue-spinner-component/archive/master.zip" class="sl-btn">Download</a>
                </div>

                <div class="sl-preview">
                    <div class="sl-preview__spinner">
                        <spinner :status="spinner.status" :color="spinner.color" :size="spinner.size" :depth="spinner.depth" :rotation="spinner.rotation" :speed="spinner.speed"></spinner>
                    </div>
                </div>
                
                <div class="sl-controls">

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
                        <input class="sl-controls__item-ctrl" type="text"  v-model="spinner.color" id="color">
                    </div>

                    <div class="sl-controls__item">
                        <label for="clockwise">Rotation</label>
                        <button class="sl-controls__item-ctrl" v-model="spinner.rotation" @click="spinner.rotation = !spinner.rotation">{{ rotationMessage }}</button>
                    </div>

                    <div class="sl-controls__item">
                        <label for="speed">Speed</label>
                        <input class="sl-controls__item-ctrl __rtl" type="range" min="0.5" max="2" step="0.1" v-model="spinner.speed" id="speed">
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
                    color: '#627794',
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
        color: #3c4858;
        min-width: 102rem;
    }

    a {
        transition: color .25s;
    }

    .app {

    }

    .sl {
        &-container {
            width: 100%;
            max-width: 86rem;
            margin: 0 auto;
        }

        &-content {
            margin: 4rem 0;
            background: #fff;
            padding: 4rem;
        }

        &-title {
            font-weight: 300;
            text-align: center;
            margin: 0 0 1rem 0;
        }

        &-subtitle {
            font-weight: 300;
            text-align: center;
            margin: 0 0 2rem 0;
        }

        &-socials {
            text-align: center;
        }

        &-preview {
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 22rem;
        }

        &-controls {
            margin-top: 2rem;

            &__item {
                margin-bottom: 2rem;
                display: flex;
                align-items: center;

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
                    background: #eff2f7;
                    padding: .6rem 1rem;
                    border-radius: .4rem;
                    outline: none;
                    transition: background .25s;
                    cursor: pointer;

                    &:hover {
                        background: darken(#eff2f7, 5%);
                    }
                }

                input[type="range"].__rtl {
                    direction: rtl
                }

            }
        }

        &-btns {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 3rem;
            margin-bottom: 2rem;
        }

        &-btn {
            display: inline-block;
            min-width: 20rem;
            font-weight: 400;
            color: #fff;
            background: #627794;
            padding: 1rem 2rem;
            border-radius: .4rem;
            transition: background .25s;
            text-align: center;
            margin: 0 1rem;
            text-decoration: none;

            &:hover {
                background: darken(#627794, 5%);
            }
        }
    }
</style>
