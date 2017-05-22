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
                        <spinner :status="spinnerStatus" :color="spinnerColor" :size="spinnerSize" :depth="spinnerDepth" :clockwise="spinnerClockwise" :speed="spinnerSpeed"></spinner>
                    </div>
                </div>
                
                <div class="sl-controls">

                    <div class="sl-controls__item">
                        <label for="size">Status</label>
                        <button class="sl-controls__item-ctrl" v-model="spinnerStatus" @click="spinnerStatus = !spinnerStatus">{{ statusMessage }}</button>
                    </div>

                    <div class="sl-controls__item">
                        <label for="size">Size</label>
                        <input class="sl-controls__item-ctrl" type="range" min="30" max="150" step="5" v-model="spinnerSize" id="size">
                    </div>

                    <div class="sl-controls__item">
                        <label for="depth">Depth</label>
                        <input class="sl-controls__item-ctrl" type="range" min="1" max="10" step="1" v-model="spinnerDepth" id="depth">
                    </div>

                    <div class="sl-controls__item">
                        <label for="color">Color</label>
                        <input class="sl-controls__item-ctrl" type="text"  v-model="spinnerColor" id="color">
                    </div>

                    <div class="sl-controls__item">
                        <label for="clockwise">Clockwise rotation</label>
                        <input class="sl-controls__item-ctrl" type="checkbox" v-model="spinnerClockwise" id="clockwise">
                    </div>

                    <div class="sl-controls__item">
                        <label for="speed">Speed</label>
                        <input class="sl-controls__item-ctrl" type="range" min="0.5" max="2" step="0.1" v-model="spinnerSpeed" id="speed">
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
                spinnerSize: 50,
                spinnerStatus: true,
                spinnerColor: '#627794',
                spinnerDepth: 3,
                spinnerClockwise: true,
                spinnerSpeed: 0.8,
            }
        },

        computed: {
            statusMessage() {
                return this.spinnerStatus ? 'Active' : 'Inactive';
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
