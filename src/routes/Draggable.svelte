<script>
    export let left = 100;
    export let top = 100;

    let moving = false;

    function onMouseDown() {
        moving = true;
    }

    function onMouseMove(e) {
        if (moving) {
            left += e.movementX;
            top += e.movementY;
        }
    }

    function onMouseUp() {
        moving = false;
    }
</script>

<div
    on:mousedown={onMouseDown}
    style="left: {left}px; top: {top}px;"
    class="draggable"
>
    <slot />
</div>

<svelte:window on:mouseup={onMouseUp} on:mousemove={onMouseMove} />

<style>
    .draggable {
        user-select: none;
        cursor: move;
        position: absolute;
    }
</style>