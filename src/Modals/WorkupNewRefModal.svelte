<script>

    import CollectionPatients from '/Users/Chris/Projects/Proj12/src/Database/CollectionPatients.svelte';
    import { createEventDispatcher } from 'svelte';

    let dispatch = createEventDispatcher();

    const showNewRefModal = (e) => {
        dispatch("showNewRefModal", e.detail);
    }

</script>



<div>
    <CollectionPatients on:showNewRefModal={showNewRefModal}/>
</div>



<style>

</style>