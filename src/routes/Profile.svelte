<script>
    import { assetUrl } from "$lib";
    import Icon from "@iconify/svelte";
    import Draggable from "./Draggable.svelte";
    
    let { username = $bindable() } = $props();
</script>

{#snippet menubar()}
    <div
        class="bg-zinc-900 pl-3 pr-1 py-1 text-sm font-semibold tracking-wide text-gray-400 flex justify-between items-center"
    >
        <span>Character</span>
        <button class="min-h-6 min-w-6 grid place-items-center">
            <Icon icon="mdi:close" class="text-xl" />
        </button>
    </div>
{/snippet}

{#snippet header()}
    <header
        class="flex gap-4 p-2 bg-zinc-800 bg-opacity-95 relative overflow-clip z-0"
    >
        <img
            src="/ui.png"
            alt=""
            class="absolute top-0 left-0 opacity-30 -z-10"
        />
        <div
            class="w-32 h-32 aspect-square shadow-md shadow-zinc-900 overflow-clip rounded-[3px] relative"
        >
            <img src="/avatar.jpg" alt="" class="h-full w-full object-cover" />
            <button
                class="absolute top-0.5 left-0.5 flex items-center gap-1 font-semibold bg-zinc-800 bg-opacity-70 rounded-[3px] p-[3px] text-lg"
            >
                <Icon icon="bxs:edit" />
            </button>
        </div>
        <div
            class="flex flex-col font-semibold justify-start content-start items-start"
        >
            <p class="text-gray-400">
                <span>From a distant future</span>
                <Icon icon="mdi:chevron-down" class="inline" />
            </p>
            <input
                type="text"
                bind:value={username}
                class="bg-transparent font-semibold text-2xl"
            />
            <p class="text-blue-400 mt-auto">
                <Icon icon="mdi:crown" class="inline -mt-1 text-lg" />
                <span>Bapharia</span>
            </p>
            <p>
                <Icon icon="mdi:chat" class="inline -mt-1 ml-0.5" />
                <span>EX SPパーティ募集中！</span>
            </p>
            <!-- <p>
                <Icon icon="mdi:pin" class="inline -mt-1 ml-0.5" />
                <span>Asteria Plains</span>
            </p> -->
        </div>
        <div class="ml-auto flex flex-col">
            <div class="flex">
                <img
                    src="{assetUrl}/UI/Icon/Award/UI_Icon_100000083.webp"
                    alt=""
                    width="54"
                    height="54"
                />
                <img
                    src="{assetUrl}/UI/Icon/Award/UI_Icon_100000102.webp"
                    alt=""
                    width="54"
                    height="54"
                />
                <img
                    src="{assetUrl}/UI/Icon/Award/UI_Icon_120000011.webp"
                    alt=""
                    width="54"
                    height="54"
                />
            </div>
            <span class="flex items-center gap-2 px-2 py-1 mt-auto">
                <img
                    src="{assetUrl}/UI/PlayerProfile/UI_PlayerProfile_LikeBtn_Pressed.webp"
                    alt=""
                    width="24"
                    height="24"
                    class="ml-auto"
                />
                <b>11,932</b>
            </span>
        </div>
    </header>
{/snippet}

{#snippet equipment(url)}
    <div
        class="equipment p-px bg-zinc-950 border-2 border-opacity-5 border-black bg-opacity-40 shadow-inner shadow-zinc-900 w-fit rounded-[4px]"
    >
        <img
            src="{assetUrl}/UI/Icon/{url}.webp"
            alt=""
            width="64"
            height="64"
        />
    </div>
{/snippet}

{#snippet loadout()}
    <div
        class="loadout p-2 flex flex-col gap-1 bg-zinc-900 bg-opacity-70 rounded-md shadow-inner shadow-zinc-900 relative group"
    >
        <!-- <div>
            <ul class="tabs flex gap-1">
                <li>Gear</li>
                <li>Skills</li>
                <li>Outfit</li>
                <li>Album</li>
            </ul>
        </div> -->

        <img
            src="/render.png"
            alt=""
            class="absolute h-[120%] bottom-0 left-1/2 -translate-x-1/2"
        />

        <div
            class="grid flex-1 gap-1 relative"
            style="grid-template-rows: 1fr 1fr 1fr 1fr 1fr; grid-template-columns: 1fr 1fr; align-items: center;"
        >
            {@render equipment("Weapon/UI_Icon_106001201")}
            {@render equipment("Imagine/Picture/UI_Icon_111002500")}
            <div></div>
            {@render equipment("Imagine/Picture/UI_Icon_112001600")}
            <div></div>
            {@render equipment("Imagine/Picture/UI_Icon_113000800")}
            {@render equipment("Imagine/Battle/UI_Icon_120000400")}
            {@render equipment("Imagine/Picture/UI_Icon_114002300")}
            {@render equipment("Imagine/Battle/UI_Icon_131001200")}
            {@render equipment("Imagine/Picture/UI_Icon_115002400")}

            <div
                class="absolute items-center flex bottom-0 left-1/2 -translate-x-1/2 text-sm opacity-50 group-hover:opacity-90 text-gray-300 -mb-0 bg-zinc-800 bg-opacity-0 group-hover:bg-opacity-70 transition-all rounded-[3px] group-hover:backdrop-blur-sm"
            >
                <div
                    class="flex gap-1 justify-center items-center py-1 pl-1 pr-2"
                >
                    <Icon icon="fluent:drag-24-filled" class="text-2xl" />
                    Rotate
                </div>
                <!-- <div class="w-px bg-zinc-100 opacity-10 h-6"></div> -->
                <div
                    class="flex gap-1 justify-center items-center py-1 pl-1 pr-2"
                >
                    <Icon icon="hugeicons:mouse-scroll-02" class="text-2xl" />
                    Zoom
                </div>
            </div>
        </div>
    </div>
{/snippet}

{#snippet stats()}
    <div
        class="overflow-y-auto max-h-[382px] rounded-md shadow-inner shadow-zinc-900"
    >
        <dl>
            <div class="!items-center !justify-normal gap-4 !py-2 !bg-zinc-900">
                <dt>
                    <img
                        src="{assetUrl}/UI/Icon/Class128/UI_IconClass128_06.webp"
                        alt=""
                        width="48"
                        height="48"
                    />
                </dt>
                <dd class="!leading-none grid -mt-1">
                    <span class="dt">Blast Archer</span>
                    <p>Lv. 90</p>
                </dd>
            </div>
            <div>
                <dt>Battle Score</dt>
                <dd>4750</dd>
            </div>
            <div>
                <dt>Attack</dt>
                <dd>851</dd>
            </div>
            <div>
                <dt>Crit Rate</dt>
                <dd>9%</dd>
            </div>
            <div>
                <dt>Crit Damage</dt>
                <dd>35%</dd>
            </div>


            
            <div>
                <dt>Health</dt>
                <dd>2142</dd>
            </div>
            <div>
                <dt>Stamina</dt>
                <dd>130</dd>
            </div>

            <div>
                <dt>Strength</dt>
                <dd>366</dd>
            </div>
            <div>
                <dt>Vitality</dt>
                <dd>302</dd>
            </div>
            <div>
                <dt>Dexterity</dt>
                <dd>251</dd>
            </div>
            <div>
                <dt>Intelligence</dt>
                <dd>283</dd>
            </div>
            <div>
                <dt>Spirit</dt>
                <dd>279</dd>
            </div>

            <div>
                <dt>Defense</dt>
                <dd>558</dd>
            </div>
            <div>
                <dt>Recovery</dt>
                <dd>617</dd>
            </div>
            <div>
                <dt>Fire Resistance</dt>
                <dd>50</dd>
            </div>
            <div>
                <dt>Thunder Resistance</dt>
                <dd>0</dd>
            </div>
            <div>
                <dt>Ice Resistance</dt>
                <dd>0</dd>
            </div>
            <div>
                <dt>Earth Resistance</dt>
                <dd>0</dd>
            </div>
            <div>
                <dt>Light Resistance</dt>
                <dd>0</dd>
            </div>
            <div>
                <dt>Dark Resistance</dt>
                <dd>0</dd>
            </div>
            
        </dl>
    </div>
{/snippet}

<Draggable>
    <div
    class="w-[650px] rounded-md absolute m-8 shadow-sm shadow-zinc-900 overflow-clip backdrop-blur-sm scale-90"
>
    {@render menubar()}
    {@render header()}
    <div
        class="grid bg-zinc-800 bg-opacity-95 relative z-0 p-2 gap-2"
        style="grid-template-columns: 1fr 250px"
    >
        <img
            src="/ui.png"
            alt=""
            class="absolute opacity-30 bottom-0 right-0 rotate-180 -z-10"
        />
        {@render loadout()}
        {@render stats()}
    </div>
</div>

</Draggable>



<style>
    .equipment:nth-of-type(2n) {
        @apply justify-self-end;
    }

    .loadout {
        background: linear-gradient(
            hsla(240, 5%, 12%, 0.7),
            hsla(240, 6%, 10%, 0.7)
        );
    }

    dl > div {
        @apply px-4 py-1 bg-zinc-900 bg-opacity-70 flex justify-between items-baseline;
    }

    dl > div:nth-of-type(2n) {
        /* @apply bg-zinc-800; */
    }

    dt, .dt {
        @apply text-sm font-semibold tracking-wider text-gray-400 uppercase;
    }

    dd {
        @apply font-semibold text-xl;
    }
</style>
