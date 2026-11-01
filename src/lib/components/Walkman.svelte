<script lang="ts">
    type soundMeta = {
        title: string
        loc: Array<number>
        desc: string
        time: string
    }
	let { items }: { items: soundMeta[] } = $props();
</script>
<div class="walkman relative w-full h-60 -top-20 rounded-[5px] bg-[linear-gradient(#497496,#44607b)] pointer-events-auto">
  <div class="walkman-right-side"></div>
  <div class="walkman-shadow-line"></div>
  <div class="sony">SONY</div>
  <div class="walkman-window">
    <div class="walkman-window-dots"></div>
    <div class="walkman-window-inner-window">
        <ol class="list-none font-disp font-semibold text-xs [font-variation-settings:'ROND'_0]">
        {#each items as item, idx}
                <li class="relative left-2">
                    <p class="mt-0.5">{item.title}</p>
                </li>
        {/each}
        </ol>
    </div>
    <div class="walkman-window-cassette">
      <div class="walkman-window-cassette-box"> 
        <div class="walkman-window-cassette-center">
          <div class="walkman-window-cassette-center-inner">
            <div class="walkman-window-cassette-center-inner-lines"></div>
            <div class="walkman-window-cassette-center-inner-lines"></div>
            <div class="walkman-window-cassette-center-inner-lines"></div>
            <div class="walkman-window-cassette-center-inner-black"></div>
            <div class="walkman-window-cassette-center-inner-black left-top"></div>
            <div class="walkman-window-cassette-center-inner-black right-top"></div>
          </div>
        </div>
      </div>
    </div>
    <div class="walkman-window-frame"> </div>
  </div>
</div> 
<style>
@import url("https://fonts.googleapis.com/css2?family=Eczar:wght@600&display=swap");
 .walkman {
	 box-shadow: 0 -3px 2px -0.5px #6d90b6 inset, 3px 0 5px 2px #6a88ac inset, 0 4.5px 3px #a6d3f9 inset, 0 30px 20px -5px rgba(0,0,0,0.1), 0 65px 50px -10px rgba(0,0,0,0.05);
}
 .walkman-right-side {
	 display: block;
	 position: absolute;
	 width: 100%;
	 height: 60px;
	 -webkit-border-radius: 0 5px 5px 0;
	 -moz-border-radius: 0 5px 5px 0;
	 border-radius: 0 5px 5px 0;
	 opacity: 0.75;
	 background: linear-gradient(#bed2dd, #a8b3be);
	 box-shadow: -2.5px -3px 4px 2px #a4bad8 inset, 0 3px 1px #d9dcf1 inset;
}
 .sony {
	 font-family: 'Eczar', serif;
	 font-size: 30px;
	 letter-spacing: 3px;
	 transform: scale(1.2, 0.8);
	 transform-origin: top;
	 display: block;
	 position: absolute;
	 height: 80%;
	 left: 50px;
	 top: 65px;
	 background: -webkit-linear-gradient(-10deg, #bacdd7 20%, #fffff9 50%, #bacdd7 60%);
	 -webkit-background-clip: text;
	 -webkit-text-fill-color: transparent;
	 filter: drop-shadow(2px 2px #49647b);
}
 .walkman-shadow-line {
	 display: block;
	 position: absolute;
	 opacity: 1;
	 left: 0;
	 top: 62px;
	 width: 100%;
	 height: 6px;
	 background: linear-gradient(#4f6c88, #0e1b33, #6d90b6 80%);
}
 .walkman-window {
	 display: block;
	 position: absolute;
	 opacity: 0.8;
	 left: 40px;
	 top: 100px;
	 width: 75%;
	 height: 100px;
	 -webkit-border-radius: 5px;
	 -moz-border-radius: 5px;
	 border-radius: 5px;
	 border: 1px solid #2a4b64;
	 background: #0f1210;
}
 .walkman-window-frame {
	 position: absolute;
	 width: 95%;
	 height: 90%;
	 left: 7px;
	 top: 5px;
	 opacity: 0.8;
	 -webkit-border-radius: 5px;
	 -moz-border-radius: 5px;
	 border-radius: 5px;
	 background-color: transparent;
	 box-shadow: 1px -2px 4px 2px #1d201e inset, 3px 0 6px 2px #262c2d inset, 0 3px 1px #6c7d85 inset;
}
 .walkman-window-dots {
	 position: absolute;
	 width: 92%;
	 height: 90%;
	 left: 12px;
	 top: 5px;
	 opacity: 0.5;
	 -webkit-border-radius: 5px;
	 -moz-border-radius: 5px;
	 border-radius: 5px;
	 background-image: radial-gradient(#232625 40%, transparent 60%);
	 background-size: 5px 5px;
}
 .walkman-window-inner-window {
	 position: absolute;
	 width: 70%;
	 height: 60px;
	 left: 65px;
	 top: 20px;
	 opacity: 0.9;
	 -webkit-border-radius: 5px;
	 -moz-border-radius: 5px;
	 border-radius: 5px;
	 background-color: #c7d6d8;
	 box-shadow: 1px -2px 5px 2px #6c7d85 inset;
}
 .walkman-window-cassette {
	 position: absolute;
	 width: 30px;
	 height: 30px;
	 left: 26px;
	 top: 33px;
	 -webkit-border-radius: 50%;
	 -moz-border-radius: 50%;
	 border-radius: 50%;
	 background-color: #73695c;
	 box-shadow: 0px -2.5px 1px 0px #403833 inset, 2px 3px 1px 0px #9f8c79 inset;
}
 .walkman-window-cassette .walkman-window-cassette-box {
	 width: 30px;
	 height: 30px;
	 left: 26px;
	 top: 20px;
	 -webkit-border-radius: 50%;
	 -moz-border-radius: 50%;
	 border-radius: 50%;
	 background-color: transparent;
	 transform-origin: center;
	 animation: playing 5s linear infinite;
}
 .btm {
	 top: 165px;
}
 .walkman-window-cassette-center {
	 position: absolute;
	 width: 22px;
	 height: 22px;
	 left: 4px;
	 top: 4px;
	 -webkit-border-radius: 50%;
	 -moz-border-radius: 50%;
	 border-radius: 50%;
	 background-color: #1f2023;
}
 .walkman-window-cassette-center-inner {
	 position: absolute;
	 width: 16px;
	 height: 16px;
	 left: 3px;
	 top: 3px;
	 -webkit-border-radius: 50%;
	 -moz-border-radius: 50%;
	 border-radius: 50%;
	 background-color: #2e3339;
}
 .walkman-window-cassette-center-inner .walkman-window-cassette-center-inner-lines:nth-child(1) {
	 transform: rotate(120deg);
}
 .walkman-window-cassette-center-inner .walkman-window-cassette-center-inner-lines:nth-child(2) {
	 transform: rotate(240deg);
}
 .walkman-window-cassette-center-inner .walkman-window-cassette-center-inner-lines:nth-child(3) {
	 transform: rotate(360deg);
}
 .walkman-window-cassette-center-inner-lines {
	 position: absolute;
	 width: 7px;
	 height: 2px;
	 left: 9px;
	 top: 7px;
	 background-color: #a0b6bf;
	 transform-origin: left;
}
 .walkman-window-cassette-center-inner-black {
	 position: absolute;
	 width: 8px;
	 height: 4px;
	 left: 12px;
	 top: 6px;
	 margin-top: 5px;
	 -webkit-border-radius: 50%;
	 -moz-border-radius: 50%;
	 border-radius: 50%;
	 background-color: #363e3e;
	 transform-origin: left;
	 transform: rotate(45deg);
}
 .right-top {
	 width: 12px;
	 left: 10px;
	 top: -1px;
	 transform: rotate(-45deg);
}
 .left-top {
	 width: 12px;
	 left: 5px;
	 top: 0px;
	 transform: rotate(180deg);
}
 @-moz-keyframes playing {
	 100% {
		 transform: rotate(360deg);
	}
}
 @-webkit-keyframes playing {
	 100% {
		 transform: rotate(360deg);
	}
}
 @-o-keyframes playing {
	 100% {
		 transform: rotate(360deg);
	}
}
 @keyframes playing {
	 100% {
		 transform: rotate(360deg);
	}
}
 
</style>