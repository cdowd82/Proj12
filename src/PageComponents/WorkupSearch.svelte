<script>

    import { createEventDispatcher } from 'svelte';
    import { Collection } from 'sveltefire';
    let dispatch = createEventDispatcher();
    let searchedPatient = "";
    let showSearchList = false;

    function toggleShowSearchList() {
        showSearchList = !showSearchList;
    };

    const dispatchSearchPatient = () => {
        dispatch('searchPatient', searchedPatient);
        searchedPatient = "";
        toggleShowSearchList(); 
    };

</script>



<div>
    <form on:submit|preventDefault={dispatchSearchPatient}>
        <input class="search-input" type="text" placeholder="Search W Patient" bind:value={searchedPatient}>
        <button type="submit">Search Workup</button>
    </form>

    <Collection path={'patients/'} let:ref={patientRef} let:data={patients}>

        {#if showSearchList}
            <div>
            <ul>
            {#each patients as { patientName, dob, journeyState}}
                {#if journeyState == 'W' && searchedPatient == patientName}
                        <li>
                            <p>{patientName} DOB: {dob}<p>
                        </li>
                {/if}
            {/each}
            <ul>
            </div>
        {/if}

    </Collection>

</div>



<style>
</style>
