<script>

    export let showNewRefModal = false;
    import { Collection } from 'sveltefire'
    import AddReferral from './AddReferral.svelte';
    import AddPatient from '/Users/Chris/Projects/Proj12/src/Database/AddPatient.svelte';

    const newRef = () => {
        showNewRefModal = !showNewRefModal;
        console.log(showNewRefModal);
    };

</script>

{#if showNewRefModal}
    <Collection path={'patients/'} let:ref={patientRef} let:data={patientsName}>
        <div>
        {#each patientsName as { patientName }}
            <div>
                { patientName }
            </div>
        {/each}
        </div>
        <AddReferral { patientRef } on:click={newRef}/>
    </Collection>
{/if}

<style></style>