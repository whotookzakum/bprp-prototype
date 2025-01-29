<script>
    let { username } = $props();

    let isInputFocused = $state(false);
    let inputEl = null;
    let chatScrollArea = null;
    let targetChannel = $state("guild");
    let chatMessages = $state([
        {
            to: "guild",
            sender: "OneCard",
            msg: "anyone want to run some sewers?",
        },
        {
            to: "zone",
            sender: "mrarm",
            msg: "hey",
        },
        {
            to: "party",
            sender: "Dewritos",
            msg: "english patch is now out!",
        },
        {
            to: "party",
            sender: "Dewritos",
            msg: "hey mrarm",
        },
        {
            to: "party",
            sender: "Dewritos",
            msg: "oops wrong chat lol",
        },
        {
            to: "whisper",
            sender: "SanGawku",
            msg: "have you finished the ui yet?",
        },
    ]);

    function focusInput() {
        inputEl.focus();
        isInputFocused = true;
    }

    function unfocusInput() {
        inputEl.blur();
        isInputFocused = false;
    }

    function onkeydown(e) {
        switch(e.key) {
            case "Enter":
                // not focused
                if (!isInputFocused) {
                    focusInput();
                }
                // focused and valid text
                else if (inputEl.value.length) {
                    submitInput();
                }
                // focused but no text
                else {
                    unfocusInput();
                }
                break
            case "Escape":
                if (isInputFocused) unfocusInput();
                break;
        }
    }

    function submitInput() {
        chatMessages = [
            ...chatMessages,
            { to: targetChannel, sender: username, msg: inputEl.value },
        ];
        inputEl.value = "";
    }

    $effect(() => {
        chatMessages;
        chatScrollArea.scrollTop = chatScrollArea.scrollHeight;
    });
</script>

<svelte:window {onkeydown} />

<div
    class="wrapper absolute w-[50ch] bg-zinc-900 bg-opacity-60 bottom-0 left-0 rounded-tr-md focus-within:bg-opacity-85 transition-all"
>
    <div></div>
    <div class="leading-relaxed text-sm">
        <ul
            id="chatContainer"
            class="px-2 py-1 max-h-[145px] overflow-y-auto"
            bind:this={chatScrollArea}
        >
            {#each chatMessages as { to, sender, msg }}
                <li data-channel={to} style:color="var(--{to})">
                    {sender}: {msg}
                </li>
            {/each}
        </ul>
        <div
            class="p-1 pl-2 border-t mt-1 border-zinc-700 border-opacity-50 items-center flex gap-1"
        >
            <button dm class="-mt-0.5" style:color="var(--guild)"
                >[Guild]</button
            >
            <input
                bind:this={inputEl}
                onclick={() => (isInputFocused = true)}
                onblur={() => (isInputFocused = false)}
                type="text"
                class="flex-1 focus:outline-none bg-zinc-900 bg-opacity-85 rounded-[3px] px-1"
            />
        </div>
    </div>
</div>

<style>
    .wrapper {
        --guild: rgb(135, 250, 135);
        --party: hsl(214, 100%, 67%);
        --whisper: hsl(352, 100%, 67%);
    }

    [data-channel]::before {
        content: "[" attr(data-channel) "] ";
        text-transform: capitalize;
    }
</style>
