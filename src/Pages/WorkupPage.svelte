<script>

    import WorkupNewRef from '/Users/Chris/Projects/Proj12/src/PageComponents/WorkupNewRef.svelte';
    import WorkupSearch from '/Users/Chris/Projects/Proj12/src/PageComponents/WorkupSearch.svelte';
    import WorkupClinic from '/Users/Chris/Projects/Proj12/src/PageComponents/WorkupClinic.svelte';
    import WorkupPreClinic from '/Users/Chris/Projects/Proj12/src/PageComponents/WorkupPreClinic.svelte';
    import { createEventDispatcher } from 'svelte';

    let dispatch = createEventDispatcher();

    const addNewRef = (e) => {
        dispatch('addNewRef', e.detail);

    };

</script>

<div>
    <h1>Workup</h1>
    <WorkupSearch/>
    <WorkupNewRef on:addNewRef={addNewRef}/>
    <WorkupPreClinic/>
    <WorkupClinic/>
</div>

<style>
    
</style>