<script>
    let moving = false;
    export let tileInfo = { x: 0, y: 0, s: 50, r: 10 };
    $: points = [
        { x: tileInfo.r, y: 0 },
        { x: tileInfo.s - tileInfo.r, y: 0 },
        { x: tileInfo.s, y: tileInfo.r },
        { x: tileInfo.s, y: tileInfo.s - tileInfo.r },
        { x: tileInfo.s - tileInfo.r, y: tileInfo.s },
        { x: tileInfo.r, y: tileInfo.s },
        { x: 0, y: tileInfo.s - tileInfo.r },
        { x: 0, y: tileInfo.r },
        { x: tileInfo.r, y: 0 },
    ];
    /* https://svelte.dev/repl/c10629261a764ae4a5c11e70ed19c5c4?version=3.29.7 */
    function startDrag() {
        moving = true;
    }
    function stopDrag() {
        moving = false;
    }
    function moveDrag(event) {
        if (moving) {
            let newTileInfo = {
                x: tileInfo.x + event.movementX,
                y: tileInfo.y + event.movementY,
                r: tileInfo.r,
                s: tileInfo.s,
            };
            tileInfo = newTileInfo;
        }
    }
</script>

<svelte:window on:mouseup={stopDrag} on:mousemove={moveDrag} />

<g transform="translate({tileInfo.x} {tileInfo.y})" on:mousedown={startDrag}>
    {#each points as point, i}<line
            stroke="black"
            x1={point.x}
            y1={point.y}
            x2={points[(i + 1) % points.length].x}
            y2={points[(i + 1) % points.length].y}
        />{/each}
</g>

<style>
    line {
        stroke: black;
        stroke-width: 3px;
        stroke-linecap: round;
    }
</style>
