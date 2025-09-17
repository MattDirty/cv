<script lang="ts">
    type EducationItem = {
        title: string,
        subtitle: string,
        school: string,
        start: string,
        end: string,
    }

    export let list: EducationItem[] = [];
</script>

{#each list as item}
    <div class="education-item">
        <h3>{item.title}</h3>
        <h4>{item.subtitle}</h4>
        <p>{item.school}</p>
        <p>{item.start} - {item.end}</p>
    </div>    
{/each}