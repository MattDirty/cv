<script lang="ts">
    export let content: string;
</script>

<p>{content}</p>

<style lang="scss">
    p {
        line-height: 1.5;
        @media print {
            line-height: unset;
        }
    }
</style>