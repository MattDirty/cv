<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import Controls from '$lib/components/Controls.svelte';
	import { mode } from '$lib/stores/mode';

    let { children }: { children?: any } = $props(); 
</script>

<svelte:head>
    <title>Mattia Torsello - CV</title>
	<link rel="icon" href={favicon} />
    {#if $mode === 'dark'}
        <style>
            @media screen {
            :root {
                --bg-color: #1e1e1e;
                --text-color: #eee;
                --highlight-color: #906;
                --link-color: #3399ff;
                --faded-text: #aaa;
            }
        }
        </style>
    {:else}
        <style>
            @media screen {
                :root {
                    --bg-color: #eee;
                    --text-color: #000;
                    --highlight-color: #ffcc00;
                    --link-color: #0066cc;
                    --faded-text: #444;
                }
            }
        </style>
    {/if}
</svelte:head>

{@render children?.()}
<div class="controls-container">
    <Controls/>
</div>


<style lang="scss">
    @media print {
        :root {
            --bg-color: #fff;
            --text-color: #000;
            --highlight-color: #ffcc00;
            --link-color: var(--text-color);
            --faded-text: #444;
        }
        .controls-container {
            display: none;
        }
    }

    :global {
        body {
            margin: 0;
            font-family: 'Fira Code', sans-serif;
            
            &.dark {
                $bg-color: #1e1e1e;
                $text-color: #ddd;
            }
            background-color: var(--bg-color);
            color: var(--text-color);
        }
        a {
            color: var(--link-color);
            text-decoration: none;
            font-weight: bolder;
        }
        h1, h2, h3, h4, p {
            margin: 0;
        }
        h1 {
            font-size: x-large;
        }
        h2 {
            font-size: large;
        }
        h3 {
            font-size: medium;
        }
        h4 {
            font-size: medium;
        }
        h4, p, ul, li {
            font-size: small;
        }
        ul {
            margin: 0;
            padding-left: 1.2rem;
        }
        h2 {
            position:relative;
            width: fit-content;
            $bg-color: var(--highlight-color);

            &::before{
                content:"";
                background-size:
                    0.25em 1em,
                    calc(100% - 0.25em * 2 + 1px) 1em,
                    0.25em 1em
                ;
                background-position:
                    left center,
                    center,
                    right center
                ;
                background-repeat: no-repeat;
                background-color: transparent;
                background-image:
                    linear-gradient(
                        to bottom right,
                        transparent 50%,
                        $bg-color 50% 100%
                    ),
                    linear-gradient(
                        to right,
                        $bg-color,
                        $bg-color
                    ),
                    linear-gradient(
                        to top left,
                        transparent 50%,
                        $bg-color 50%
                    );
                width:100%;
                height:0.5em;
                position:absolute;
                z-index:-1;
                left:-0.25em;
                bottom:0.1em;
                padding:0 0.25em;
                }
        }
}
</style>