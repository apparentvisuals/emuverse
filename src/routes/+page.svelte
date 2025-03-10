<script lang="ts">
import { invoke } from "@tauri-apps/api/core";
import AButton from "$lib/AButton.svelte";
import PlusButton from "$lib/PlusButton.svelte";
import { onMount } from "svelte";

let time = $state(new Date());
let timeString = $derived(time.toLocaleTimeString(navigator.language, { hour12: false, hour: '2-digit', minute: '2-digit' }));

let name = $state("");
let greetMsg = $state("");

async function greet(event: Event) {
  event.preventDefault();
  // Learn more about Tauri commands at https://tauri.app/develop/calling-rust/
  greetMsg = await invoke("greet", { name });
}

onMount(() => {
  const interval = setInterval(() => {
    time = new Date();
  });
  return () => {
    clearInterval(interval);
  }
});
</script>

<main class="h-screen w-screen flex flex-col dark">
  <section class="header flex justify-between items-center mx-[6em] px-[2em] pt-[3em]">
    <div class="profiles flex gap-[1.5em]">
      <button class="size-[6em] rounded-full border-[.25em] border-[#504F4E] shadow-md"><img class="rounded-full" src="/img/profiles/link.png" alt="profile link"/></button>
      <button class="size-[6em] rounded-full border-[.25em] border-[#504F4E] shadow-md"><img class="rounded-full" src="/img/profiles/mario.png" alt="profile mario"/></button>
      <button class="size-[6em] rounded-full border-[.25em] border-[#504F4E] shadow-md"><img class="rounded-full" src="/img/profiles/starfox.png" alt="profile starfox"/></button>
    </div>    
    <div class="status gap-[1.5em] flex">
      <div class="text-[2em]">{timeString}</div>
      <div class="text-[2em]">88<span class="text-[0.6em]">%</span></div>
    </div>
  </section>
  <section class="content grow">
    <div class="content-items flex items-center gap-[1.3em] px-[10em] py-[2em] overflow-x-auto h-full">
      <button class="element game" style="background-image: url('/img/games/zelda.png'); background-size: cover;" aria-label="zelda">
        <div class="hidden absolute text-[#2DB4EA] text-[2.7em] top-[-2em] left-[-1.5em] right-[-10em] text-left">Animal Crossing: New Horizons</div>
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element game" style="background-image: url('/img/games/smashbros.png'); background-size: cover;" aria-label="smashbros">
        <div class="hidden absolute text-[#2DB4EA] text-[2.7em] top-[-2em] left-[-1.5em] right-[-10em] text-left">Animal Crossing: New Horizons</div>
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element game" style="background-image: url('/img/games/odyssey.png'); background-size: cover;" aria-label="odyssey">
        <div class="hidden absolute text-[#2DB4EA] text-[2.7em] top-[-2em] left-[-1.5em] right-[-10em] text-left">Animal Crossing: New Horizons</div>
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element game" style="background-image: url('/img/games/crossing.png'); background-size: cover;" aria-label="crossing">
        <div class="hidden absolute text-[#2DB4EA] text-[2.7em] top-[-2em] left-[-1.5em] right-[-10em] text-left">Animal Crossing: New Horizons</div>
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element game" aria-label="none">
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element game" aria-label="none">
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element game" aria-label="none">
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element game" aria-label="none">
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element game" aria-label="none">
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element game" aria-label="none">
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element game" aria-label="none">
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element game" aria-label="none">
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
      <button class="element" aria-label="all software">
        <div class="hidden animate-borderColor pointer-events-none absolute inset-[-.95em] rounded-[.2em] border-[.5em]"></div>
      </button>
    </div>
  </section>
  <nav class="sections flex gap-[2em] justify-center mx-[6em] py-[6em]">
    <button class="size-[7em] rounded-full first:bg-[#E70013] bg-[#505050]" aria-label="store"><img src="/img/nav/online.svg" alt="nintendo online"/></button>
    <button class="size-[7em] rounded-full first:bg-[#E70013] bg-[#505050]" aria-label="controllers"><img src="/img/nav/controllers.svg" alt="controller"/></button>
    <button class="size-[7em] rounded-full first:bg-[#E70013] bg-[#505050]" aria-label="system settings"><img src="/img/nav/settings.svg" alt="settings"/></button>
    <button class="size-[7em] rounded-full first:bg-[#E70013] bg-[#505050]" aria-label="power"><img src="/img/nav/sleep.svg" alt="sleep"/></button>
  </nav>

  <div class="footer flex justify-end gap-12 border-t-2 mx-[6em] py-[2em] px-[3em]">
    <button class="text-[2em] flex gap-2 items-center"><AButton c="size-[1.5em]"/>Continue</button>
    <button class="text-[2em] flex gap-2 items-center"><PlusButton c="size-[1.5em]"/>Start</button>
  </div>

</main>

<style lang="postcss">
@reference "tailwindcss";

.content-items::-webkit-scrollbar {
  display: none;
}
.content-items {
  scrollbar-width: 0px;
  -ms-overflow-style: none;
}

.content .element {
  @apply h-full aspect-square min-h-[128px] max-h-[512px] relative;
  :focus {
    outline: none;
  }
}

.content .game {
  @apply border-[#504F4E] border-[.25em];
}

.content .game:focus {
  > div {
    @apply block;
  }
}
.profiles {
  > button:focus {
    outline: none;
    animation: borderColorChange .9s infinite;
  }
}
nav {
  > button {
    > img {
      @apply w-full h-full;
    }
  }
  > button:focus {
    outline: none;
    animation: borderColorChange .9s infinite;
    @apply border-[.25em];
  }
}
</style>
