<script lang="ts">
    import { lang } from '$lib/stores/lang';

	import Summary from '$lib/components/Summary.svelte';
	import TheHeader from '$lib/components/TheHeader.svelte';
    import Education from '$lib/components/Education.svelte';
	import FlatList from '$lib/components/FlatList.svelte';
	import List from '$lib/components/List.svelte';
	import WorkExperience from '$lib/components/WorkExperience.svelte';

    import me from '$lib/data/me.json';
    import summary from '$lib/data/summary.json';
    import education from '$lib/data/education.json';
    import techSkills from '$lib/data/tech_skills.json';
    import languages from '$lib/data/languages.json';
    import hobbies from '$lib/data/hobbies.json';
    import workExp from '$lib/data/work.json';
    import projects from '$lib/data/projects.json';
</script>


<div class="page">
    <TheHeader {...me[$lang]} />
    <main>
        <aside>
            <section>
                <h2>{education[$lang].title}</h2>
                <Education list={education[$lang].items}/>
            </section>
            <section>
                <h2>{techSkills[$lang].title}</h2>
                <FlatList list={techSkills[$lang].items} />
            </section>
            <section>
                <h2>{languages[$lang].title}</h2>
                <List list={languages[$lang].items.map((item) => {return `${item.language} - ${item.level}`})} />
            </section>
            <section class="hobbies">
                <h2>Hobbies</h2>
                {#each hobbies[$lang] as hobby}
                <section>
                    <h3>{hobby.category}</h3>
                    <List list={hobby.items} />
                </section>
                {/each}
            </section>
            <footer>
                <h2>
                    {$lang === 'fr' ? 'Références disponibles sur demande' : 'References available upon request'}
                </h2>
                <h2 class="for-print">
                    {$lang === 'fr' ? 'Retrouvez moi en ligne sur cv.le-dahu-stud.io' : 'Find me online at cv.le-dahu-stud.io'}
                </h2>
            </footer>       
        </aside>
        <div class="main-content">
            <section>
                <h2>{summary[$lang].title}</h2>
                <Summary {...summary[$lang]} />
            </section>
            <section>
                <h2>{workExp[$lang].title}</h2>
                <WorkExperience items={workExp[$lang].items}/>
            </section>
            <section>
                <h2>{projects[$lang].title}</h2>
                <WorkExperience items={projects[$lang].items}/>
            </section>
        </div>
    </main>
</div>

<style lang="scss">
    .page {
        box-sizing: border-box;
        max-width: 1000px;
        margin: 0 auto;
        box-shadow: 0 0 10px rgba(0,0,0,0.1);
        padding: 1rem 2rem;

        @media print {
            box-shadow: none;
            max-width: 100%;
            margin: 0;
            padding: 0;
        }
    }

    main {
        margin-top: 1rem;
        display: flex;
        gap: 2rem;
        flex-direction: row;
        justify-content: space-between;
        flex-wrap: nowrap;

        @media print {
            gap: 1rem;
            margin-top: 0.5rem;
            .hobbies {
                break-inside: avoid;
            }
        }
    }
    aside {
        display: flex;
        flex-direction: column;
        border-right: 2px solid #333;
        padding-right: 1rem;
        width: 30%;
        margin-bottom: 1rem;

        @media print {
            footer {
                margin-top: 13rem;
            }
        }

    }
    .main-content {
        width: 80%;
    }
    section {
        margin-bottom: 1rem;
    }
</style>