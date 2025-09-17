<script lang="ts">
    export let list: string[] = ["Skill 1", "Skill 2", "Skill 3"];
</script>

<ul class="skills-list">
    {#each list as skill}
        <li>{skill}</li>
    {/each}
</ul>

<style lang="scss">
    ul {
        list-style: none;
        padding: 0;
        display: flex;
        flex-wrap: wrap;
    }
    li::after {
        margin: 0 0.5rem;
        content: '/';
    }
    li:last-child::after {
        content: '';
    }
</style>