<script>

    export let patients;
    export let patientRef;

    function handle() {
        console.log("H");
    }
</script>


<div>
    <ul class="no-bullets">
        {#each patients as { patientName, dob, journeyState, firstName, lastName}}
            {#if ((journeyState == 'W') && (firstName != "") && (lastName != ""))}
                <li on:click={handle}>
                    {patientName} DOB: {dob} Journey State: {journeyState} 
                </li>
            {/if}
        {/each}
    </ul>
</div>


<style>

    ul.no-bullets {
        list-style-type: none; /* Remove bullets */
        padding: 0; /* Remove padding */
        margin: 50px; /* Remove margins */
        text-align: left;

    }
</style>
