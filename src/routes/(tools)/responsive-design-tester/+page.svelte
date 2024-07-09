<script>
  import { faTabletScreenButton } from "@fortawesome/free-solid-svg-icons";
  import { faRotateLeft } from "@fortawesome/free-solid-svg-icons";
  import { FontAwesomeIcon } from "@fortawesome/svelte-fontawesome";
  import { faDesktop } from "@fortawesome/free-solid-svg-icons";
  import { faMobile } from "@fortawesome/free-solid-svg-icons";
  $: defaultHeight = null;
  $: defaultWidth = null;
  $: inputUrl = "";
  $: storedUrl = "";
  $: resDesktopIconClicked = false;
  $: resTabletIconClicked = false;
  $: resPhoneIconClicked = false;

  let mobile = [
    { common: { width: 360, height: 640 } },
    { iphone6_to_8: { width: 375, height: 667 } },
    { larger: { width: 375, height: 720 } },
    { iphoneX: { width: 375, height: 812 } },
    { google_pixel_2: { width: 411, height: 731 } },
  ];
  //i want to render a mini-sidebar such that when we click on the icons, it will show the various screens available

  let resolutionObject = {
    twenty_two_inch_height: 1920,
    twenty_two_inch_width: 1200,
  };

  function dropDownPage(inputUrl) {
    defaultHeight = 3840;
    defaultWidth = 2160;

    //3840
    //2160
    //1920
    //1080
    //https://learn.svelte.dev/tutorial/welcome-to-svelte

    storedUrl = inputUrl;
  }
  $:count = 0;
  
  function incrementForDesktop() {    
    if(count % 2 == 0)  resDesktopIconClicked = true;
    else resDesktopIconClicked = false;
    count += 1;
  }

  function incrementForTablet() {
    count += 1;
    if(count % 2 == 0)  incrementForDesktop = true;
    else incrementForDesktop = false;
  }

  function incrementForPhone() {
    count += 1;
    if(count % 2 == 0)  resPhoneIconClicked = true;
    else resPhoneIconClicked = false;
  }

</script>

<div
  class="container mx-auto max-w-screen-xl flex flex-col lg:flex-row overflow-hidden rounded-lg"
>
  <!-- Add tool here -->
  <div
    class="side bg-blue-300 w-40 shadow-xl h-screen p-5 flex flex-col items-center py-48"
  >
    <!--<button>
      <FontAwesomeIcon class="w-14 h-14" icon={faRotateLeft} style="top"/>
    </button>-->    
      
    <button on:click={incrementForDesktop}>
      <FontAwesomeIcon class="w-14 h-14" icon={faDesktop} />
      {resDesktopIconClicked}      
    </button>
    
    
    <button>
      <FontAwesomeIcon class="w-14 h-14" icon={faDesktop} />
    </button>
    <button class="flex flex-col justify-between items-center py-4">
      <FontAwesomeIcon class="w-14 h-14" icon={faMobile} />
    </button>

    <button class="fa-bars">
      <FontAwesomeIcon class="w-14 h-14" icon={faTabletScreenButton} />
    </button>
  </div>
  <main class="flex-1 p-5">
    <div class="input-area mt-16 flex flex-row items-center">
      <input
        type="text"
        bind:value={inputUrl}
        placeholder=""
        class="input-url"
      />
      <button
        on:click={() => dropDownPage(inputUrl)}
        class="bg-black hover:bg-black-900 text-white w-11 h-11 rounded"
        >Go</button
      >
    </div>
    <div class="content mt-10 overflow-hidden max-h-auto">
      <object
        type="text/html"
        data={storedUrl}
        width={defaultWidth}
        height={defaultHeight}
        title="drop-down-page"
      >
      </object>
    </div>
  </main>
</div>

<style>
  .container {
    background-color: white;
  }
  .side {
    box-shadow: 0 -1px 15px 2px rgb(0 0 0 / 0.7);
  }
  .fa-bars {
    color: rgb(0, 0, 0);
  }
  .input-url {
    background-color: rgb(183, 231, 233);
    color: rgb(71, 69, 69);
    padding: 10px;
    padding-right: 0;
    border: none;
    border-radius: 5px;
    width: 100%;
  }
  @media (min-width: 1024px) {
    .container {
      flex-direction: row;
    }
  }
  .input-area {
    display: flex;
    gap: 10px; /* Adjust gap as needed */
    align-items: center;
    width: 100%;
  }

  .content {
    max-height: 625px;
    max-width: 1080px;
    overflow-y: auto;
    overflow-x: auto;
    border: 5px ridge blue;
  }
</style>
