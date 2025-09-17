<script lang="ts">
    type WorkItem = {
        title: string,
        company: string,
        period: string,
        description: string,
        points: string[],
    }

    export let items: WorkItem[] = [];
</script>

{#each items as item}
    <div class="work-item">
        <h3>{item.title}</h3>
        <h4>{item.company}</h4>
        <p class="period">{item.period}</p>
        <p>{item.description}</p>
        {#if item.points.length > 0}
            <ul>
                {#each item.points as point}
                    <li>{point}</li>
                {/each}
            </ul>
        {/if}
    </div>    
{/each}

<style lang="scss">
    .work-item {
        position: relative;
        margin-bottom: 1rem;
        h3, h4 {
            margin: 0;
        }
        .period {
            font-style: italic;
            color: var(--faded-text);
            margin-bottom: 0.5rem;
        }
        ul {
            margin: 0.5rem 0 0 0.5rem;
        }
        @media print {
            margin-bottom: 0.5rem;
            .period {
                margin-bottom: 0.2rem;
            }

            ul {
                margin: 0rem 0 0 0.5rem;
            }
        }
    }
</style>