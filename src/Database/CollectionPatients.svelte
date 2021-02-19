<script>

    let showNewRefModal = false;
    import { Collection , Doc } from 'sveltefire'
    import AddReferral from './AddReferral.svelte';

    let showWorkupList = false;

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

        <!-- Add referral -->
        {#if showNewRefModal}
            <AddReferral { patientRef } on:click={newRef} {showNewRefModal} on:toggleShowNewRefModal={newRef}/>
        {/if}
        <p on:click={newRef}>New Referral</p>

    </Collection>

<style>
</style>