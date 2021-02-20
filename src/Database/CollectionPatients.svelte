<script>

    let showNewRefModal = false;
    import { Collection , Doc } from 'sveltefire'
    import AddReferral from './AddReferral.svelte';

    const newRef = () => {
        showNewRefModal = !showNewRefModal;
        console.log(showNewRefModal);
    };

</script>

    <Collection path={'patients/'} let:ref={patientRef}>

        <!-- Add referral -->
        {#if showNewRefModal}
            <AddReferral {patientRef} on:click={newRef} {showNewRefModal} on:toggleShowNewRefModal={newRef}/>
        {/if}
        <p on:click={newRef}>New Referral</p>

    </Collection>

<style>

</style>