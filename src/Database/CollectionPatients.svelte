<script>

    import { Collection} from 'sveltefire'
    import AddReferral from './AddReferral.svelte';
    import { createEventDispatcher }from 'svelte';

    let dispatch = createEventDispatcher();
    let showNewRefModal = false;

    const newRef = () => {
        showNewRefModal = !showNewRefModal;
        console.log(showNewRefModal);
        dispatch('showNewRefModal', showNewRefModal);
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