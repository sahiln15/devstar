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
  function resolutionUpdate(height, width) {
    defaultHeight = height;
    defaultWidth = width;
  }
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
  $: count = 0;

  function incrementForDesktop() {
    if (count % 2 == 0) resDesktopIconClicked = true;
    else resDesktopIconClicked = false;
    count += 1;
  }

  function incrementForTablet() {
    count += 1;
    if (count % 2 == 0) incrementForDesktop = true;
    else incrementForDesktop = false;
  }

  function incrementForPhone() {
    count += 1;
    if (count % 2 == 0) resPhoneIconClicked = true;
    else resPhoneIconClicked = false;
  }
</script>

<div
  class="container mx-auto max-w-screen-xl flex flex-col lg:flex-row overflow-hidden rounded-lg"
>
  {#if resDesktopIconClicked == true}
    <div
      class=" side hover:bg-emerald-400 bg-emerald-300 w-40 shadow-xl h-screen p-5 flex flex-col items-center py-48"
    >
      <button
        on:click={() => resolutionUpdate(1920, 1200)}
        class="w-40 hover:bg-emerald-500"
      >
        <ul class=" submenu-desktop">
          <li style="color: black" class="submenu-title">
            24" Desktop<br />
            <p style="color: blue;" class="resolution">1920x1200</p>
          </li>
        </ul>
      </button>
      <button
        on:click={() => resolutionUpdate(1920,1080)}
        class="w-40 hover:bg-emerald-500"
      >
        <ul class=" submenu-desktop">
          <li style="color: black" class="submenu-title">
            23" Desktop<br />
            <p style="color: blue;" class="resolution">1920x1080</p>
          </li>
        </ul>
      </button>
      <button
        on:click={() => resolutionUpdate(1680,1050)}
        class="w-40 hover:bg-emerald-500"
      >
        <ul class=" submenu-desktop">
          <li style="color: black" class="submenu-title">
            22" Desktop<br />
            <p style="color: blue;" class="resolution">1680x1050</p>
          </li>
        </ul>
      </button>
      <button
        on:click={() => resolutionUpdate(1920, 1200)}
        class="w-40 hover:bg-emerald-500"
      >
        <ul class=" submenu-desktop">
          <li style="color: black" class="submenu-title">
            21.5" Desktop<br />
            <p style="color: blue;" class="resolution">1080x1920</p>
          </li>
        </ul>
      </button>
      <button
        on:click={() => resolutionUpdate(1600,900)}
        class="w-40 hover:bg-emerald-500"
      >
        <ul class=" submenu-desktop">
          <li style="color: black" class="submenu-title">
            20" Desktop<br />
            <p style="color: blue;" class="resolution">1600x900</p>
          </li>
        </ul>
      </button>
      <button
        on:click={() => resolutionUpdate(1440,900)}
        class="w-40 hover:bg-emerald-500"
      >
        <ul class=" submenu-desktop">
          <li style="color: black" class="submenu-title">
            19" Desktop<br />
            <p style="color: blue;" class="resolution">1440x900</p>
          </li>
        </ul>
      </button>
      <button
        on:click={() => resolutionUpdate(1366,768)}
        class="w-40 hover:bg-emerald-500"
      >
        <ul class=" submenu-desktop">
          <li style="color: black" class="submenu-title">
            15" Desktop<br />
            <p style="color: blue;" class="resolution">1366x768</p>
          </li>
        </ul>
      </button>
      <button
        on:click={() => resolutionUpdate(1024,800)}
        class="w-40 hover:bg-emerald-500"
      >
        <ul class=" submenu-desktop">
          <li style="color: black" class="submenu-title">
            13" Desktop<br />
            <p style="color: blue;" class="resolution">1024x800</p>
          </li>
        </ul>
      </button>
      <button
        on:click={() => resolutionUpdate(1024,600)}
        class="w-40 hover:bg-emerald-500"
      >
        <ul class=" submenu-desktop">
          <li style="color: black" class="submenu-title">
            10" Desktop<br />
            <p style="color: blue;" class="resolution">1024x600</p>
          </li>
        </ul>
      </button>
      
    </div>
  {/if}

  

  <!-- Add tool here -->
  <div
    class="side bg-blue-300 w-40 shadow-xl h-screen p-5 flex flex-col items-center py-48"
  >
    <!--<button>
      <FontAwesomeIcon class="w-14 h-14" icon={faRotateLeft} style="top"/>
    </button>-->

    

    <button on:click={incrementForDesktop}>
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
    max-height: 100%;
    max-width: 100%;
    border: 5px ridge blue;
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

  .submenu-desktop {
    align-items: center;
    width: 100%;
    gap: 10px;
    padding-right: 0;
    border: none;
    border-radius: 5px;
  }
</style>
