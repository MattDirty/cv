<script lang="ts">
    import { lang } from '$lib/stores/lang';
    import { mode } from '$lib/stores/mode';
    import locs from './ControlsLocalisation.json';
    import { derived } from 'svelte/store';

    const tr = derived(lang, $lang => locs[$lang]);

    const toggleLang = () => {
        lang.update(current => current === 'en' ? 'fr' : 'en');
    }

    const toggleLightMode = () => {
        mode.update(current => current === 'light' ? 'dark' : 'light');
        document.body.className = $mode;
    }
</script>

<div class="controls">
    <button onclick={toggleLang}>{$tr.switchLanguage}</button>
    <button onclick={toggleLightMode}>{$mode === 'light' ? $tr.darkMode : $tr.lightMode}</button>
    <button onclick={() => { window.print() }}>{$tr.print}</button>
    <button onclick={() => {}}>{$tr.seeSource}</button>
</div>

<style lang="scss">
    .controls {
        position: fixed;
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
        bottom: 1rem;
        right: 1rem;
        background: rgba(255, 255, 255, 0.8);
        border: 1px solid #ccc;
        border-radius: 0.5rem;
        padding: 0.5rem;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        z-index: 1000;
    }
</style>