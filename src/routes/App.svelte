<script>

import images1 from '../images/1.png';
import images2 from '../images/2.png';
import images3 from '../images/3.png';
import images4 from '../images/4.png';
import images5 from '../images/5.png';
import images6 from '../images/6.png';
import images7 from '../images/7.png';
import images8 from '../images/8.png';
import images9 from '../images/9.png';
import images10 from '../images/10.png';
import images11 from '../images/11.png';


    let currId = 0;
    const images = [
        images1,
      images2,
      images3,
      images4,
      images5,
      images6,
      images7,
      images8,
      images9,
      images10,
      images11

    ];
    const imgLen = images.length;
    let positionLeft = 0;
  
    const moveSlider = () => {
      positionLeft = currId * 100;
    };
  
    const next = () => {
      currId = currId === imgLen - 1 ? 0 : currId + 1;
      moveSlider();
    };
      
    const prev = () => {
      currId = currId === 0 ? imgLen - 1 : currId - 1;
      moveSlider();
    };
  
    const getIndex = (/** @type {number} */ index) => {
      currId = index;
      moveSlider();
    };
  
      let interval = setInterval(next, 4000);
      const autoPlay = () => {
          interval = setInterval(next, 4000)
      }
  
      const stopPlay = () => {
          clearInterval(interval)
      }
  </script>
  
  <main>
    <!-- <h1>Svelte Image Carousel Slider</h1> -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <!-- svelte-ignore a11y-mouse-events-have-key-events -->
    <div on:mouseover={stopPlay} on:mouseleave={autoPlay} class="container">
      <div class="slider" style="left: -{positionLeft}%;">
        {#each images as img}
          <img src={img} alt="" />
        {/each}
      </div>
      <div class="arrow">
        <button on:click={prev} class="prev">◀</button>
        <button on:click={next} class="next">▶</button>
      </div>
      <div class="papagination">
        {#each images as _, i}
          <button
            class={currId === i ? 'active' : ''}
            on:click={() => getIndex(i)}
          />
        {/each}
      </div>
    </div>
    <!-- <p>
      Images from pixabay : <a
        href="https://pixabay.com/"
        target="_blank"
        rel="noopener">https://pixabay.com/</a
      >
    </p> -->
  </main>
  
  <style>
    main {
      padding: 15px;
      text-align: center;
    }
    .container {
      position: relative;
      width: 100%;
      max-width: 1040px;
      
      margin: 0 auto;
      overflow: hidden;
    }
    .slider {
      display: flex;
      position: relative;
      transition: left 0.5s;
    }
    .slider img {
      width: 100%;
      height: auto;
      object-fit: cover;
      flex-shrink: 0;
    }
    .arrow {
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
    }
    .arrow button {
      margin-bottom: 0;
      padding: 12px;
      border: 0;
      background-color: rgba(255, 255, 255, 0.7);
      cursor: pointer;
    }
  
    .papagination {
      position: absolute;
      bottom: 0;
      padding-bottom: 8px;
      width: 100%;
    }
  
    .papagination button {
      margin: 0 4px;
      width: 14px;
      height: 14px;
      border: 0;
      border-radius: 50%;
      background-color: gray;
      text-align: center;
      cursor: pointer;
    }
    .papagination .active {
      background-color: rgba(255, 0, 0, 0.8);
    }
  </style>
  