<script>
    
    import { onMount } from "svelte";
    let panel;

    onMount(() => {
        const pickr = Pickr.create({
            el: '.color-picker',
            theme: 'nano', 

            swatches: [
                'rgba(244, 67, 54, 1)',
                'rgba(233, 30, 99, 0.95)',
                'rgba(156, 39, 176, 0.9)',
                'rgba(103, 58, 183, 0.85)',
                'rgba(63, 81, 181, 0.8)',
                'rgba(33, 150, 243, 0.75)',
                'rgba(3, 169, 244, 0.7)',
                'rgba(0, 188, 212, 0.7)',
                'rgba(0, 150, 136, 0.75)',
                'rgba(76, 175, 80, 0.8)',
                'rgba(139, 195, 74, 0.85)',
                'rgba(205, 220, 57, 0.9)',
                'rgba(255, 235, 59, 0.95)',
                'rgba(255, 193, 7, 1)'
            ],

            components: {
                preview: true,
                opacity: true,
                hue: true,

                interaction: {
                    hex: true,
                    rgba: true,
                    hsla: true,
                    hsva: true,
                    cmyk: true,
                    input: true,
                    clear: true,
                    save: true
                }
            }
        });

        pickr.on('change', (...args) => {
            let color = args[0].toRGBA();
            panel.style.backgroundColor = `rgba(${color[0]},${color[1]},${color[2]},${color[3]})`;
        });
    });
</script>

<header>
    <h1 class="heading">Color Picker</h1>
</header>

<div class="panel container" bind:this={panel}></div>
<div class="color-picker"></div>

<style>
    .panel {
        width: 100%;
        height: 40vh;
        margin-bottom: 20px;
        margin-top: 20px;
        background-color: rgb(210, 219, 30);
    }

    .heading {
        margin-top: 0px;
        margin-bottom: 10px;
        max-width: fit-content;
        margin-left: auto;
        margin-right: auto;
        font-family: Papyrus, fantasy;
        font-size: 3rem;
        background: linear-gradient(to right, #ef5350, #f48fb1, #7e57c2, #2196f3, #26c6da, #43a047, #eeff41, #f9a825, #ff5722);
        background-clip: text;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
    }

    .footer {
        position: fixed;
        left: 0;
        bottom: 0;
        width: 100%;
        background-color: azure;
        color: black;
        text-align: center;
    }
</style>

<footer class="footer">Made by Nischal Basavaraju</footer>
