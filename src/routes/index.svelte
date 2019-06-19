<script>
  import { onMount } from "svelte";
  import PlayButton from "../components/PlayButton.svelte";
  let seconds = 10;
  let minutes = 12;

  onMount(() => {
    const interval = setInterval(() => {
      if (seconds === 0) {
        seconds = 60;
        minutes -= 1;
      } else {
        seconds -= 1;
      }
    }, 1000);

    return () => clearInterval(interval);
  });
</script>

<style>
  :global(*) {
    margin: 0;
    padding: 0;
    font-family: "Oswald";
  }

  .side-info {
    position: fixed;
    left: 0;
    bottom: 0;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    grid-area: sideinfo;
    transform: rotate(270deg) translateY(55vh);
    transform-origin: left bottom;
    font-weight: bold;
    line-height: 1;
    padding-left: 4vh;
  }

  .matches {
    position: fixed;
    right: 0;
    top: 20vh;
    list-style: none;
    width: 40vw;
    font-size: 8vh;
    padding: 2rem;
  }

  .matches > li:first-of-type {
    border-top: 1px solid #111;
  }

  .matches > li {
    display: grid;
    grid-template-columns: 3em 1fr 3em;
    width: 100%;
    justify-content: space-between;
    border-bottom: 1px solid #111;
  }
  .red > img,
  .blue > img {
    height: 8vh;
    margin: 0 3vh;
  }

  .red {
    text-align: end;
  }

  .VS {
    text-align: center;
  }

  .time {
    font-size: 35vh;
    line-height: 1.2;
  }

  .season {
    font-size: 8vh;
    transform: scaleX(2.3);
    transform-origin: left;
  }
  .week {
    font-size: 4vh;
    font-weight: initial;
  }

  main {
    box-sizing: border-box;
    padding: 1rem;
    color: #111;
    background: linear-gradient(to top right, #4262ab, #19d9bb 50%);
    height: 100vh;
    text-transform: uppercase;
  }

  .partners {
    display: flex;
    flex: 1;
  }

  .partners > *,
  .music > * {
    padding: 1rem 1rem;
  }

  .top {
    display: flex;
  }

  .music {
    white-space: nowrap;
    overflow-x: hidden;
  }

  .partners > :first-child {
    border-right: 2px solid #222;
  }

  .partners ul {
    list-style: none;
    display: flex;
    flex: 1;
    grid-gap: 3rem;
  }

  .music {
    display: flex;
    justify-content: flex-end;
  }
</style>

<main>
  <div class="top">
    <div class="partners">
      <h2>Official Partners</h2>
      <ul>
        <li>FootLocker</li>
        <li>Shell</li>
        <li>Logitech</li>
        <li>DXRacer</li>
      </ul>
    </div>
    <div class="music">
      <p>Pentakill - Tear of the Goddess</p>
    </div>
  </div>
  <div class="side-info">
    <div class="time"> {minutes}:{seconds > 9 ? seconds : '0' + seconds} </div>
    <div class="season">Summer 19</div>
    <div class="week">week one</div>
  </div>
  <ol class="matches">
    <li>
      <div class="blue">
        <img src="g2.png" alt="G2" />
      </div>
      <div class="VS">VS</div>
      <div class="red">
        <img src="spy.png" alt="Splyce" />
      </div>
    </li>
    <li>
      <div class="blue">
        <img src="og.png" alt="Origen" />
      </div>
      <div class="VS">VS</div>
      <div class="red">
        <img src="vit.png" alt="Vitality" />
      </div>
    </li>
    <li>
      <div class="blue">
        <img src="rge.png" alt="Rogue" />
      </div>
      <div class="VS">VS</div>
      <div class="red">
        <img src="msf.png" alt="Misfits" />
      </div>
    </li>
    <li>
      <div class="blue">
        <img src="/fnc.png" alt="Fnatic" />
      </div>
      <div class="VS">VS</div>
      <div class="red">
        <img src="sk.png" alt="SK" />
      </div>
    </li>
    <li>
      <div class="blue">
        <img src="s04.png" alt="Schalke 04" />
      </div>
      <div class="VS">VS</div>
      <div class="red">
        <img src="xl.png" alt="Excel" />
      </div>
    </li>
  </ol>
</main>
