<script>
    import ColorDisplay from '$lib/ColorDisplay.svelte';

    let selectedColor = $state("Blue");

    function selectColor(color) {
        selectedColor = color;
    }
</script>


    <h1>My Preference</h1>

    <p>Choose a color:</p>

    <button onclick={() => selectColor("Blue")}>
        Blue
    </button>

    <button onclick={() => selectColor("Green")}>
        Green
    </button>

    <button onclick={() => selectColor("Red")}>
        Red
    </button>

    <ColorDisplay color={selectedColor} />
