let timer = 10; //初期設定時間
let countdownInterval = null; 
let count = 0; //クリック数
let gameStarted = false; //ゲーム開始フラグ 開始中true
let initialTimer = 0;
const music = new Audio('gameEnd.mp3'); //ゲーム終了♪
const music2 = new Audio('gameStart.mp3'); //ゲーム終了♪

const tenSec = document.getElementById("tenSec");
const fifteenSec = document.getElementById("fifteenSec");
const thirtySec = document.getElementById("thirtySec");
const countdown = document.getElementById("countdown");

// ゲーム中にボタンを無効化する関数
function disableButtons() {
  tenSec.disabled = true;
  fifteenSec.disabled = true;
  thirtySec.disabled = true;
}

// ゲーム中にボタンを有効化する関数
function enableButtons() {
  tenSec.disabled = false;
  fifteenSec.disabled = false;
  thirtySec.disabled = false;
}


// ゲームをリセットする関数
function resetGame() {
  clearInterval(countdownInterval);
  gameStarted = false;
  timer = initialTimer || 10;
  count = 0;
  counter.innerText = count;
  countdown.innerText = `Time：${timer}s`;
  clickButton.innerText = "スペースキーでstart!"
  enableButtons();
}

//制限時間を設定する
function timerSet(sec){
  if (gameStarted === false) {
  initialTimer = sec;
  timer = initialTimer;
  count = 0;
  counter.innerText = count;
  countdown.innerText = `Time：${timer}s`
  clickButton.innerText = "スペースキーでstart!"
  }
}

tenSec.addEventListener("click", function(){timerSet(10)});
fifteenSec.addEventListener("click", function(){timerSet(15)});
thirtySec.addEventListener("click", function(){timerSet(30)});

//Clickイベントの処理
const counter = document.getElementById("counter");
const clickButton = document.getElementById("clickbutton");

function clickCounter() {
  if (gameStarted === true) {
  count++;
  counter.innerText = count;
  }
}

clickButton.addEventListener("mousedown", clickCounter);


//3秒後にカウントダウンを開始(ゲームを開始)
function startTimer() {
  music2.currentTime = 0;
  music2.play();
  setTimeout(function() {
    
    if (gameStarted === false) {

      if (timer === 10 || timer === 15 || timer === 30) {
        disableButtons();
        gameStarted = true;
        countdownInterval = setInterval(function() {
          timer--;
          countdown.innerText = "Time：" + timer + "s";

          if (timer === 0) {
            clearInterval(countdownInterval);
            music.currentTime = 0;
            music.play();
            clickButton.disabled = true;
            setTimeout(function () { 
              alert("TimeUp！\nscore：" + count);
              resetGame(); }, 100)
          }

        }, 1000);
        
      } else {
        alert("制限時間を選択してください");
      }
    }

  }, 3000);
}

document.addEventListener("keydown", function(event) {
  if (event.code === "Space") {
    if (gameStarted === false) {
      clickButton.innerText = "ここを押しまくれ！"
      startTimer();
    }
  }
});
