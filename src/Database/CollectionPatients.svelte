<script>

    let showNewRefModal = false;
    import { Collection , Doc } from 'sveltefire'
    import AddReferral from './AddReferral.svelte';
    import Counter from '/Users/Chris/Projects/Proj12/src/Counter.svelte';

    let showWorkupList = false;
    let count;

    const newRef = () => {
        showNewRefModal = !showNewRefModal;
        console.log(showNewRefModal);
    };

    const showPatientsList = () => {
        showWorkupList = !showWorkupList;
        console.log(showWorkupList);
    }

     
</script>

    <Collection path={'patients/'} let:ref={patientRef} let:data={patients}>

        <!-- Render for workup -->
        <p on:click={showPatientsList}>Show patients</p>
        {#if showWorkupList}
            <div>
            <ul>
            {#each patients as { patientName, dob, journeyState}, i}
                {#if journeyState == 'W'}
                    <li>
                        <p>{patientName} DOB: {dob}<p>
                    </li>
                {/if}
            {/each}
            <ul></ul>
            </div>
        {/if}

        <!-- Add referral -->
        {#if showNewRefModal}
            <AddReferral { patientRef } on:click={newRef} {showNewRefModal} on:toggleShowNewRefModal={newRef}/>
        {/if}
        <p on:click={newRef}>New Referral</p>

    </Collection>

<style>

</style>