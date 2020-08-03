<template>
  <div class="clock" data-clock>
    <div class="hand hour" data-hour-hand></div>
    <div class="hand minute" data-minute-hand></div>
    <div class="hand second" data-second-hand></div>

    <div class="number number1">
      <p>1</p>
    </div>
    <div class="number number2">
      <p>2</p>
    </div>
    <div class="number number3">
      <p>3</p>
    </div>
    <div class="number number4">
      <p>4</p>
    </div>
    <div class="number number5">
      <p>5</p>
    </div>
    <div class="number number6">
      <p>6</p>
    </div>
    <div class="number number7">
      <p>7</p>
    </div>
    <div class="number number8">
      <p>8</p>
    </div>
    <div class="number number9">
      <p>9</p>
    </div>
    <div class="number number10">
      <p>10</p>
    </div>
    <div class="number number11">
      <p>11</p>
    </div>
    <div class="number number12">
      <p>12</p>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Clock',
  mounted: function () {
    this.updateTime()
    window.setTimeout(() => {
      this.fadeIn()
    }, 1000)
  },
  methods: {
    updateTime() {
      window.setInterval(() => {
        const currentDate = new Date()
        const secondsRatio = currentDate.getSeconds() / 60
        const minutesRatio = (secondsRatio + currentDate.getMinutes()) / 60
        const hoursRatio = (minutesRatio + currentDate.getHours()) / 12

        const secondHand = document.querySelector('[data-second-hand]')
        const minuteHand = document.querySelector('[data-minute-hand]')
        const hourHand = document.querySelector('[data-hour-hand]')

        secondHand.style.setProperty('--rotation', secondsRatio * 360)
        minuteHand.style.setProperty('--rotation', minutesRatio * 360)
        hourHand.style.setProperty('--rotation', hoursRatio * 360)

      }, 1000)
    },
    fadeIn() {
      var op = 0.1;
      var element = document.querySelector('[data-clock]')
      element.style.display = 'block';
      var timer = setInterval(function () {
        if (op >= 1){
            clearInterval(timer);
        }
        element.style.opacity = op;
        element.style.filter = 'alpha(opacity=' + op * 100 + ")";
        op += op * 0.1;
      }, 10)
    }
  }
}
</script>

<style scoped>
.clock {
  width: 400px;
  height: 400px;
  position: relative;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, .6);
  border: 5px solid var(--gray1);

  background: radial-gradient(var(--gray7), var(--gray6));
  box-shadow: 7px 10px 2px rgba(0,0,0, 0.1) inset;

  margin: 3rem auto;

  -moz-user-select:none;
  -webkit-user-select:none;
  -webkit-touch-callout:none;
  -ms-user-select:none;
  user-select:none;
  opacity: 0;
}

.clock::before {
  content: '';
  height: 400px;
  width: 400px;
  position: absolute;
  border-radius: 50%;
  box-shadow: 7px 10px 3px rgba(0,0,0, 0.2);
}

.clock::after {
  content: '';
  height: 15px;
  width: 15px;
  position: absolute;
  top: 50%;
  left: 50%;
  border-radius: 50%;
  transform: translate(-50%, -50%);
  z-index: 11;
  background-color: var(--gray1);
}

.clock .number {
  position: absolute;
  width: 100%;
  height: 100%;
  text-align: center;
  font-size: 3em;
  font-family: 'Cinzel', serif;
  color: var(--gray1);
  transform: rotate(var(--rotation));
}

.clock .number p {
  margin: 0;
  padding: 0;
  transform: rotate(var(--rotation));
}

.clock .number1 { --rotation: 30deg; }
.clock .number1 p { --rotation: -30deg; }

.clock .number2 { --rotation: 60deg; }
.clock .number2 p { --rotation: -60deg; }

.clock .number3 { --rotation: 90deg; }
.clock .number3 p { --rotation: -90deg; }

.clock .number4 { --rotation: 120deg; }
.clock .number4 p { --rotation: -120deg; }

.clock .number5 { --rotation: 150deg; }
.clock .number5 p { --rotation: -150deg; }

.clock .number6 { --rotation: 180deg; }
.clock .number6 p { --rotation: -180deg }

.clock .number7 { --rotation: 210deg; }
.clock .number7 p { --rotation: -210deg; }

.clock .number8 { --rotation: 240deg; }
.clock .number8 p { --rotation: -240deg; }

.clock .number9 { --rotation: 270deg; }
.clock .number9 p { --rotation: -270deg; }

.clock .number10 { --rotation: 300deg; }
.clock .number10 p { --rotation: -300deg; }

.clock .number11 { --rotation: 330deg; }
.clock .number11 p { --rotation: -330deg; }

.clock .hand {
  --rotation: 0;
  position: absolute;
  bottom: 50%;
  left: 50%;
  width: 10px;
  height: 40%;
  background-color: var(--gray1);
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
  transform-origin: bottom;
  transform: translateX(-50%) rotate(calc(var(--rotation) * 1deg));
  z-index: 10;
  box-shadow: 2px 2px rgba(0,0,0, 0.2);
}

.clock .hand.hour {
  width: 10px;
  height: 25%;
}

.clock .hand.minute {
  width: 7px;
  height: 40%;
}

.clock .hand.second {
  width: 3px;
  background-color: red;
  height: 45%;
  z-index: 1;
}

</style>
