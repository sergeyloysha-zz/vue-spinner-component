<template>
  <div class="sl-spinner" v-show="status" :style="spinnerStyle"></div>
</template>

<script>
  export default {
    props: {
      status: {
        type: Boolean,
        default: true
      },

      rotation: {
        type: Boolean,
        default: true
      },

      size: {
        type: Number,
        default: 30
      },

      depth: {
        type: Number,
        default: 3
      },

      speed: {
        type: Number,
        default: 1.0
      },

      color: {
        type: String,
        default: '#6589b6'
      },

      opacity: {
        type: Number,
        default: -1
      }
    },

    data() {
      return {
        rotationAnimations: ['forward', 'backward'],
        sizeUnits: 'px',
        timeUnits: 's'
      }
    },

    computed: {
      rotationDirection() {
        return this.rotation ? this.rotationAnimations[0] : this.rotationAnimations[1];
      },

      spinnerSize() {
        return this.size + this.sizeUnits;
      },

      spinnerDepth() {
        return this.depth + this.sizeUnits;
      },

      spinnerSpeed() {
        return this.speed + this.timeUnits;
      },

      spinnerPrimaryOpacity() {
        return this.opacity === 1 ? 0.99 : this.opacity;
      },

      spinnerSecondaryOpacity() {
        return this.opacity < 0 ? 0.15 : (this.opacity/100)*15;
      },

      spinnerStyle() {
        return {
          borderTopColor: this.hexToRGB(this.color, this.spinnerSecondaryOpacity),
          borderRightColor: this.hexToRGB(this.color, this.spinnerSecondaryOpacity),
          borderBottomColor: this.hexToRGB(this.color, this.spinnerSecondaryOpacity),
          borderLeftColor: this.opacity < 0 ? this.color : this.hexToRGB(this.color, this.spinnerPrimaryOpacity),
          width: this.spinnerSize,
          height: this.spinnerSize,
          borderWidth: this.spinnerDepth,
          animationName: this.rotationDirection,
          animationDuration: this.spinnerSpeed
        }
      }
    },
    methods: {
      hexToRGB(hex, alpha) {
        var r = parseInt(hex.slice(1, 3), 16),
            g = parseInt(hex.slice(3, 5), 16),
            b = parseInt(hex.slice(5, 7), 16);

        if (alpha) {
            return `rgba(${r}, ${g}, ${b}, ${alpha})`;
        } else {
            return `rgb(${r}, ${g}, ${b})`;
        }
      }
    }
  }
</script>

<style lang="scss">

  .sl-spinner {
    border-style: solid;
    -webkit-transform: translateZ(0);
    -ms-transform: translateZ(0);
    transform: translateZ(0);

    animation-iteration-count: infinite;
    animation-timing-function: linear;

    border-radius: 50%;
    width: 30px;
    height: 30px;
  }

  @keyframes forward {

      0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
      }

      100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
      }

  }

  @keyframes backward {

    0% {
      -webkit-transform: rotate(0deg);
      transform: rotate(0deg);
    }

    100% {
      -webkit-transform: rotate(360deg);
      transform: rotate(-360deg);
    }

  }

</style>