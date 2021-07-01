<template>
    <section class="counter">
        <div class="counter__img"> <img src="../../public/image/bomb.png" alt="bomb"></div>
        <div class="counter__item"> <div class="counter__time">{{hours}}</div><div class="counter__title"> Hours </div></div>
        <div class="counter__item"> <div class="counter__time">{{minutes}}</div><div class="counter__title"> Minutes </div> </div>
        <div class="counter__item"> <div class="counter__time">{{seconds}} </div> <div class="counter__title"> Secounds </div> </div>
    </section>

    <div class="buttons">
    <button class="buttons__item" @click="start"> Start / Continue </button>
    <button class="buttons__item" @click="stop"> Stop </button>
    <button class="buttons__item" @click="reset"> Reset </button>
    </div>
</template>

<script>
    import {ref} from 'vue';
    export default {
        setup() {
            let hours = ref(0);
            let minutes = ref(1);
            let seconds = ref(0);
            let timer = "";

            function start(){
                stop();
                    timer = setInterval(() => {
                    if (seconds.value > 0) {
                        seconds.value --;
                    }
                    else if (seconds.value == 0 && minutes.value > 0) {
                        seconds.value = 59;
                        minutes.value--;
                    }
                    else if (seconds.value == 0 && minutes.value == 0 && hours.value > 0) {
                        seconds.value = 59;
                        minutes.value = 59;
                        hours.value --;
                    }else if (seconds.value == 0 && minutes.value == 0 && hours.value == 0){
                    
                        // let gong = new Audio("../../public/sounds/bomb.mp3");
                        // gong.play();
                        alert("please reset to try again!");
                        clearInterval(timer);
                    }
            },1000);

            }

            function stop() {
                clearInterval(timer);
            }

            function reset() {
            hours.value = 0;
            minutes.value = 1;
            seconds.value = 0;
            }

             return {
                hours,
                minutes,
                seconds,
                timer,
                start,
                stop,
                reset,
            }
        },
 
    }
</script>

<style lang="scss">
    .counter {

        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        color: #f5f5f5;
        font-size: 40px;
        padding-bottom: 30px;
        &__time {
            padding: 5px;
            background: #f5f5f5;
            width: 150px;
            border-radius: 20px;
            margin-right: 10px;
            color: #333;
            margin-bottom: 10px;
        }

        &__img {
            width: 300px;
            position: absolute;
            left: -100px;
            top: -150px;
            & > img {
                width: 100%;
                display: block;
            }
        }

        &__title {
            font-size: 20px;
        }
        
        }

        .buttons {
            display: flex;
            flex-direction: row;
            margin-top: 50px;
            justify-content: center;
     
            &__item {
                width: 150px;
                padding: 18px;
                border-radius: 30px;
                border: none;
                outline: none;
                cursor: pointer;
                color: #f5f5f5;
                font-size: 16px;
                transition: 0.3s;

                &:hover {

                transform: translateY(-3px);
                }

                &:nth-child(1) {
                    background: green;
                    margin-right: 20px;

                    &:hover {
                        box-shadow: 1px 4px 14px 8px rgba(0,128,0,0.44);
                        
                        }

                    }
                &:nth-child(2) {
                    background: red;
                    margin-right: 20px;
                    
                     &:hover {
                        
                        box-shadow: 1px 4px 14px 8px rgba(255,0,0,0.44);
                        }
                }
                &:nth-child(3) {
                    background: blue;
            
                    
                     &:hover {
                        box-shadow: 1px 4px 14px 8px rgba(0, 19, 128, 0.44);
                        }
                }

                
                }
            }
</style>