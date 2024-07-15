<script>
//載入圖片
import rock from '@/assets/img/rock.png'
import paper from  '@/assets/img/paper.png'
import scissors from  '@/assets/img/scissors.png'

export default {
    //初始值
    data() {
        return {
            rock: rock,
            paper:paper,
            scissors:scissors,
            score:{
                wins:0,
                losses:0,
                ties:0
            },
            youResult:'',
            computerResult:'',
            result:'',
        }
    },
    //執行方法
    methods: {
        pickComputerMove(){
            const randomNumber = Math.random();
            let computerMove = "";
            if (randomNumber >= 0 && randomNumber < 1 / 3) {
                computerMove = "rock";
            } else if (randomNumber >= 1 / 3 && randomNumber < 2 / 3) {
                computerMove = "paper";
            } else if (randomNumber >= 2 / 3 && randomNumber < 1) {
                computerMove = "scissors";
            }
            return computerMove;
        },
        playGame(playerMove){
            const computerMove = this.pickComputerMove();
            if (computerMove === "rock") {
                this.computerResult = this.rock;
            } else if (computerMove === "paper") {
                this.computerResult = this.paper;
            } else if (computerMove === "scissors") {
                this.computerResult = this.scissors;
            }

            if (playerMove === "scissors") {
                this.youResult = this.scissors;
            if (computerMove === "rock") {
                this.result = "你輸了";
            } else if (computerMove === "paper") {
                this.result = "你贏了";
            } else if (computerMove === "scissors") {
                this.result = "平手";
            }
            } else if (playerMove === "paper") {
                this.youResult = this.paper;
            if (computerMove === "rock") {
                this.result = "你贏了";
            } else if (computerMove === "paper") {
                this.result = "平手";
            } else if (computerMove === "scissors") {
                this.result = "你輸了";
            }
            } else if (playerMove === "rock") {
                this.youResult = this.rock;
            if (computerMove === "rock") {
                this.result = "平手";
            } else if (computerMove === "paper") {
                this.result = "你輸了";
            } else if (computerMove === "scissors") {
                this.result = "你贏了";
            }
            }

            if (this.result === "你贏了") {
                this.score.wins += 1;
            } else if (this.result === "你輸了") {
                this.score.losses += 1;
            } else if (this.result === "平手") {
                this.score.ties += 1;
            }
            },
        },
}

</script>

<template>

<main class="bg-cyan-50">
    <div class="text-center">
        <h1 class="text-3xl bg-cyan-200">猜拳遊戲</h1>
        <p class="mt-5">
            局數：
            贏了 {{this.score.wins}}局
            輸了 {{this.score.losses}}局
            平手 {{this.score.ties}}局
        </p>
    </div>

    <div class="flex justify-center mt-[50px] p-[50px] bg-sky-400">
            <div class="text-center mr-[20px]">
                <p>電腦</p>
                <img :src="computerResult" class="move-icon h-[100px]">
            </div>
            <div class="w-[100px] text-center text-2xl ">
                <p class="mt-[50px] bg-amber-200">{{ result }}</p>
            </div>
            <div class="text-center ml-[20px]">
                <p>你</p>
                <img :src="youResult" class="move-icon h-[100px]">
            </div>
    </div>
    <p class="flex justify-center mt-5">請選擇</p>
    
    <div class="flex justify-center">
        <div class="">
            <button type="button" class="move-button" @click="playGame('rock')">
                <img :src="rock" class="h-[100px]" alt="">
            </button>
        </div>
        <div class="">
            <button type="button" class="move-button" @click="playGame('paper')">
                <img :src="paper" class="h-[100px]" alt="">
            </button>
        </div>
        <div class="">
            <button type="button" class="move-button" @click="playGame('scissors')">
                <img :src="scissors" class="h-[100px]" alt="">
            </button>
        </div>
    </div>
    
    
</main>

</template>

<style>

</style>
