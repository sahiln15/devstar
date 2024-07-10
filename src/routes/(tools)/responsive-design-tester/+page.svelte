<script>
    import { onMount } from 'svelte';
  
    let menuOpen = false;
    let selectedDevice = '';
    let url = '';
    let devices = [];
  
    const phoneDevices = [
      { name: 'iPhone SE', width: 375, height: 667 },
      { name: 'iPhone 12 Pro', width: 390, height: 844 },
      { name: 'Pixel 5', width: 393, height: 851 },
    ];
  
    const tabletDevices = [
      { name: 'iPad Mini', width: 768, height: 1024 },
      { name: 'iPad Air', width: 820, height: 1180 },
      { name: 'iPad Pro', width: 1024, height: 1366 },
    ];
  
    const computerDevices = [
      { name: 'Laptop', width: 1280, height: 800 },
      { name: 'Desktop', width: 1920, height: 1080 },
      { name: 'Large Monitor', width: 2560, height: 1440 },
    ];
  
    function toggleMenu() {
      menuOpen = !menuOpen;
    }
  
    function selectDevice(type) {
      selectedDevice = type;
      devices = type === 'phone' ? phoneDevices :
                type === 'tablet' ? tabletDevices :
                computerDevices;
    }
  
    function checkUrl() {
      if (!url.startsWith('http://') && !url.startsWith('https://')) {
        url = 'https://' + url;
      }
    }
  
    onMount(() => {
      // Any initialization code if needed
    });
  </script>
  
  <main>
    <header>
      <button on:click={toggleMenu} class="menu-button">☰</button>
      <h1>Responsive Design Tester</h1>
    </header>
  
    {#if menuOpen}
      <nav class="menu">
        <button on:click={() => selectDevice('phone')}>Phone</button>
        <button on:click={() => selectDevice('tablet')}>Tablet</button>
        <button on:click={() => selectDevice('computer')}>Computer</button>
      </nav>
    {/if}
  
    <div class="url-input">
      <input type="text" bind:value={url} placeholder="Enter URL to test">
      <button on:click={checkUrl}>Check</button>
    </div>
  
    {#if selectedDevice}
      <div class="devices-container">
        {#each devices as device}
          <div class="device">
            <h3>{device.name}</h3>
            <iframe 
  title={device.name} 
  src={url} 
  width={device.width} 
  height={device.height}
></iframe>
          </div>
        {/each}
      </div>
    {/if}
  </main>
  
  <style>
    :global(body) {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }
  
    header {
      background-color: #333;
      color: white;
      padding: 1rem;
      display: flex;
      align-items: center;
    }
  
    .menu-button {
      background: none;
      border: none;
      color: white;
      font-size: 1.5rem;
      cursor: pointer;
      margin-right: 1rem;
    }
  
    h1 {
      margin: 0;
    }
  
    .menu {
      background-color: #f0f0f0;
      padding: 1rem;
      display: flex;
      justify-content: space-around;
    }
  
    .menu button {
      padding: 0.5rem 1rem;
      cursor: pointer;
    }
  
    .url-input {
      display: flex;
      justify-content: center;
      margin: 2rem 0;
    }
  
    .url-input input {
      width: 60%;
      padding: 0.5rem;
    }
  
    .url-input button {
      padding: 0.5rem 1rem;
      cursor: pointer;
    }
  
    .devices-container {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 2rem;
      padding: 2rem;
    }
  
    .device {
      border: 1px solid #ccc;
      padding: 1rem;
      text-align: center;
    }
  
    iframe {
      border: 1px solid #999;
      resize: both;
      overflow: auto;
    }
  </style>
