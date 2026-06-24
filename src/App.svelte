<script lang="ts">
  import { animate, utils } from 'animejs';
  import { onMount } from 'svelte';
  import asterik from './assets/new_logo_small.png';
  import LITATF from './LITATF.svelte';
  import SIC from './SIC.svelte';

  let LITATFSchedule: HTMLDivElement;
  let SICSchedule: HTMLDivElement;

  const toggleClassIfFound = (ele: Element, className: string) =>
    ele.classList.contains(className) ? ele.classList.toggle(className) : null;
  const toggleClassIfNotFound = (ele: Element, className: string) =>
    !ele.classList.contains(className) ? ele.classList.toggle(className) : null;

  const animateLITATF = () => {
    const allListItems = document.querySelectorAll(
      '#LITATFCont > ul.collapsible > li',
    );
    animate(allListItems, {
      translateY: [250, 0],
      opacity: [0, 1],
      easing: 'easeInOutExpo',
      duration: 500,
      delay: utils.stagger(150),
    });
  };

  const animateSIC = () => {
    const allListItems = document.querySelectorAll(
      '#SICCont > ul.collapsible > li',
    );
    animate(allListItems, {
      translateY: [250, 0],
      opacity: [0, 1],
      easing: 'easeInOutExpo',
      duration: 500,
      delay: utils.stagger(150),
    });
  };
  let LITATFBtn: HTMLButtonElement;
  let SICBtn: HTMLButtonElement;

  function init() {
    const lastChose = window.localStorage.getItem('lastChose');
    if (lastChose !== undefined) {
      if (lastChose === 'LITATF') {
        animateLITATF();
        toggleClassIfNotFound(LITATFBtn, 'chosen');
        toggleClassIfFound(LITATFSchedule, 'hidden');
        return;
      }
      if (lastChose === 'SIC') {
        toggleClassIfNotFound(SICBtn, 'chosen');
        toggleClassIfFound(SICSchedule, 'hidden');
        toggleClassIfNotFound(LITATFSchedule, 'hidden');
        animateSIC();
      }
    }
  }

  const LITATFClicked = (e: Event) => {
    if (LITATFSchedule.classList.contains('hidden')) {
      toggleClassIfFound(LITATFSchedule, 'hidden');
      toggleClassIfNotFound(SICSchedule, 'hidden');
      window.localStorage.setItem('lastChose', 'LITATF');
      animateLITATF();
      if (!LITATFBtn.classList.contains('chosen')) {
        LITATFBtn.classList.toggle('chosen');
      }
      if (SICBtn.classList.contains('chosen'))
        SICBtn.classList.toggle('chosen');
    }
  };

  const SICClicked = (e: Event) => {
    if (SICSchedule.classList.contains('hidden')) {
      toggleClassIfFound(SICSchedule, 'hidden');
      toggleClassIfNotFound(LITATFSchedule, 'hidden');
      window.localStorage.setItem('lastChose', 'SIC');
      animateSIC();
      if (!SICBtn.classList.contains('chosen')) {
        SICBtn.classList.toggle('chosen');
      }
      if (LITATFBtn.classList.contains('chosen'))
        LITATFBtn.classList.toggle('chosen');
    }
  };

  onMount(() => {
    init();
  });
</script>

<main class="container">
  <div id="anchor"></div>
  <div class="row">
    <div class="col s12 center">
      <div class="title mainheader">
        <img id="titleAsterikL" src={asterik} alt="ASC Asterik" />
        All Star Code PD Bootcamp Schedule
        <img id="titleAsterikR" src={asterik} alt="ASC Asterik" />
      </div>
    </div>
  </div>
  <div class="button-cont">
    <button
      class="waves-effect waves-light btn btn-large schedule-btn"
      on:click={LITATFClicked}
      bind:this={LITATFBtn}
    >
      LI / TA / TF
    </button>
    <button
      class="waves-effect waves-light btn btn-large schedule-btn"
      on:click={SICClicked}
      bind:this={SICBtn}
    >
      SIC
    </button>
  </div>
  <ul class="collapsible">
    <div id="LITATFCont" class="hidden" bind:this={LITATFSchedule}>
      <LITATF />
    </div>
    <div id="SICCont" class="hidden" bind:this={SICSchedule}>
      <SIC />
    </div>
  </ul>
  <button
    id="scrollToTop"
    class="waves-effect waves-light btn btn-medium"
    on:click={() =>
      document.getElementById('anchor')!.scrollIntoView({ behavior: 'smooth' })}
  >
    back to top
  </button>
</main>
