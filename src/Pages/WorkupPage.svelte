<script>

    import WorkupNewRef from '/Users/Chris/Projects/Proj12/src/PageComponents/WorkupNewRef.svelte';
    import WorkupSearch from '/Users/Chris/Projects/Proj12/src/PageComponents/WorkupSearch.svelte';
    import WorkupClinic from '/Users/Chris/Projects/Proj12/src/PageComponents/WorkupClinic.svelte';
    import WorkupPreClinic from '/Users/Chris/Projects/Proj12/src/PageComponents/WorkupPreClinic.svelte';
    import WorkupShowPatients from '/Users/Chris/Projects/Proj12/src/PageComponents/WorkupShowPatients.svelte';

    // display logic variables
    let showNewRef;
    let showWorkupPatients;

    // display logic functions
    const showNewRefModal = (e) => {
        showNewRef = e.detail;
    }

    const showWorkupPatientList = (e) => {
        showWorkupPatients = e.detail;
    }

</script>



<div>
    {#if !showNewRef && !showWorkupPatients}
            <h1>Workup</h1>
    {/if}

    {#if !showNewRef && !showWorkupPatients}
            <WorkupSearch/>
    {/if}

    {#if !showWorkupPatients} 
        <WorkupNewRef on:showNewRefModal={showNewRefModal}/>
    {/if}

    <!--
    <WorkupPreClinic/>
    <WorkupClinic/>
    -->

    {#if !showNewRef}
        <WorkupShowPatients on:showWorkupPatientList={showWorkupPatientList}/>
    {/if}
</div>



<style>
    
</style>