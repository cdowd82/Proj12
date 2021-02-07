<script>

    import WorkupNewRefModal from '/Users/Chris/Projects/Proj12/src/Modals/WorkupNewRefModal.svelte';

    import { createEventDispatcher } from 'svelte';

    let dispatch = createEventDispatcher();

    let showNewRefModal = false;

    const newRef = () => {
        showNewRefModal = !showNewRefModal;
        console.log(showNewRefModal);
    };

    const addNewRef = (e) => {
        dispatch('addNewRef', e.detail);
    };

</script>

<div>
    <WorkupNewRefModal {showNewRefModal} on:click={newRef} on:addNewRef={addNewRef}/>
    <p on:click={newRef}>New Referral</p>
</div>

<style>

</style>