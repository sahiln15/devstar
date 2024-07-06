<script>
    import { faRotateLeft } from "@fortawesome/free-solid-svg-icons";
    import { FontAwesomeIcon } from "@fortawesome/svelte-fontawesome";
    import { faShareNodes } from "@fortawesome/free-solid-svg-icons";
    import { faBars } from "@fortawesome/free-solid-svg-icons";
    $: defaultHeight = null;
    $: defaultWidth = null;
    $: url = "";
    let outputUrl = "";

    let resolutionObject = {
      
      twenty_two_inch_height: 1920,
      twenty_two_inch_width: 1200,
    }

    function dropDownPage(url){
      defaultHeight = 1920;
      defaultWidth = 1080;
      outputUrl = "https://tailwindcss.com/docs/customizing-colors";
    }

</script>

<div class="container mx-auto max-w-screen-xl flex flex-col lg:flex-row overflow-hidden rounded-lg">
    <!-- Add tool here -->
    <!-- <div class="bg-light-gray overflow-y-auto py-5 px-3 h-full border-r border-gray-200">  -->
    <div class="side bg-blue-300 w-40 shadow-xl h-screen p-5 flex flex-col items-center sticky top-0">
        <div class="flex-1 flex flex-col items-center">
            <button>
                <FontAwesomeIcon class="w-14 h-14" icon={faRotateLeft} />
            </button>
            <button class="flex flex-col justify-between items-center py-24 text-lg">
                <FontAwesomeIcon class="w-14 h-14" icon={faBars} />MENU
            </button>
        </div>
        <button class="fa-bars">
            <FontAwesomeIcon class="w-14 h-14" icon={faShareNodes} />
        </button>
    </div>
    <main class="flex-1 p-5">
        <div class="input-area mt-16 flex flex-row items-center">
            <input bind:innerHTML={url} contenteditable type="text" placeholder="" class="input-url" />
            <button on:click={()=>dropDownPage(url)} class="bg-black hover:bg-black-900 text-white w-11 h-11 rounded">Go</button>
        </div>
        
        <div class="content mt-10">
          <!-- New UI elements will be added here -->
          <iframe src={outputUrl} height={defaultHeight} width={defaultWidth} title="drop-down-page"></iframe>
          
      </div>
    </main>
</div>

<style>
  .container{
      background-color: white;
  }
  .side {
      box-shadow: 0 -1px 15px 2px rgb(0 0 0 / 0.7);
  }
  .fa-bars {
      color: rgb(139, 139, 148);
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
</style>