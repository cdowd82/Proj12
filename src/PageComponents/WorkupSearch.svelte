<script>

    import { createEventDispatcher } from 'svelte';
    import { Collection } from 'sveltefire';
    let dispatch = createEventDispatcher();
    let searchedPatient = "";
    let showSearchList = true;

    function toggleShowSearchList() {
        showSearchList = !showSearchList;
    };

    const dispatchSearchPatient = () => {
        console.log("search search");
        console.log(showSearchList);
        console.log(searchedPatient);
        searchedPatient = "";
    };

</script>



<div>

    <Collection path={'patients/'} let:ref={patientRef} let:data={patients}>

        <form on:submit|preventDefault={dispatchSearchPatient}>
            <input class="search-input" type="text" placeholder="Search W Patient" bind:value={searchedPatient}>
        </form>

        {#if searchedPatient != ""}
            <div>
            <ul class="no-bullets">
                {#each patients as { patientName, dob, journeyState, firstName, middleNames, lastName}}
                        {#if (searchedPatient == patientName && journeyState == "W")
                            || (searchedPatient == firstName && journeyState == "W")
                            || (searchedPatient == lastName && journeyState == "W")
                            || (searchedPatient == (firstName + ' ' + lastName) && journeyState == "W")
                            || (searchedPatient == (firstName + ' ' + middleNames) && journeyState == "W")
                        }
                                <li>
                                    <p>{patientName}   DOB: {dob}   Journey State: {journeyState}<p>
                                </li>
                    {/if}
                {/each}
            <ul>
            </div>
        {/if}
        
    </Collection>

</div>



<style>
        ul.no-bullets {
        list-style-type: none; /* Remove bullets */
        padding: 0; /* Remove padding */
    }
</style>
