<template>

    <div class="sl">
        <div class="sl-container">
            <div class="sl-content">
                <h1 class="sl-title">VueJS Spinner Component</h1>

                <div class="sl-preview">
                    <div class="sl-preview__spinner">
                        <spinner :status="spinnerStatus" :color="spinnerColor" :size="spinnerSize" :depth="spinnerDepth" :clockwise="spinnerClockwise" :duration="spinnerDuration"></spinner>
                    </div>
                </div>
                
                <div class="sl-controls">

                    <div class="sl-controls__item">
                        <label for="size">Spinner Status</label>
                        <button v-model="spinnerStatus" @click="spinnerStatus = !spinnerStatus">{{ statusMessage }}</button>
                    </div>

                    <div class="sl-controls__item">
                        <label for="size">Spinner Size</label>
                        <input type="range" min="30" max="150" step="5" v-model="spinnerSize" id="size">
                    </div>

                    <div class="sl-controls__item">
                        <label for="depth">Spinner Depth</label>
                        <input type="range" min="1" max="10" step="1" v-model="spinnerDepth" id="depth">
                    </div>

                    <div class="sl-controls__item">
                        <label for="color">Spinner Color</label>
                        <input type="text"  v-model="spinnerColor" id="color">
                    </div>

                    <div class="sl-controls__item">
                        <label for="clockwise">Spinner Clockwise rotation</label>
                        <input type="checkbox" v-model="spinnerClockwise" id="clockwise">
                    </div>

                    <div class="sl-controls__item">
                        <label for="duration">Spinner Duration</label>
                        <input type="range" min="0.5" max="2" step="0.1" v-model="spinnerDuration" id="duration">
                    </div>

                </div>

            </div>
        </div>
    </div>

</template>

<script>

    import Spinner from './components/Spinner.vue'

    export default {
        components: {
            Spinner
        },

        data() {
            return {
                spinnerSize: 40,
                spinnerStatus: true,
                spinnerColor: '#627794',
                spinnerDepth: 3,
                spinnerClockwise: true,
                spinnerDuration: 1.1,
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
        font: 400 1.4rem/1.4 'Helvetica Neue', Arial, sans-serif;
        color: #3c4858;
        min-width: 102rem;
    }

    a {
        transition: color .25s;
    }

    .app {

        &__inner {
            padding: 8.9rem 4rem 2rem 4rem;
        }

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
            font-weight: 400;
            text-align: center;
            margin: 0 0 4rem 0;
        }

        &-preview {
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 22rem;
        }

        &-controls {


            &__item {
                margin-bottom: 2rem;
                display: flex;
                align-items: center;

                label {
                    min-width: 10rem;
                    margin-right: 2rem;
                }
            }
        }
    }
</style>
