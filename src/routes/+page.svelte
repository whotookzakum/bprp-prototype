<script>
    import Chat from "./Chat.svelte";
    import Profile from "./Profile.svelte";

    let username = $state("Zakum");
    let showProfile = $state(true);

    // Need various blockers, like if the user is focused on an input and typing, block window toggling. also need to bind this state so that the x button can also close, etc.
    // function onkeydown(e) {
    //     switch(e.key) {
    //         case "u":
    //             showProfile = !showProfile
    //     }
    // }
</script>

<svelte:window {onkeydown} />

<div class="fixed top-0 left-1/2 -translate-x-1/2 -z-50 h-screen aspect-video">
    <img src="/bg1.png" alt="" />
    <Chat {username} />
    {#if showProfile}
        <Profile bind:username />
    {/if}
</div>
