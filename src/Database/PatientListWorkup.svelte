<script>
    
    export let patients;
    export let patientsRef;
    export let showWorkupPatientList = false;

    function handle() {
        console.log(patients[i].id);
    }

</script>



{#if showWorkupPatientList}
    <div class="list-BD" on:click|self>
        <div class="list-modal">
            <ul class="no-bullets">
                {#each patients as { patientName, dob, journeyState, firstName, lastName, id}, i}
                    {#if ((journeyState == 'W') && (firstName != "") && (lastName != ""))}
                        <li>
                            {patientName} DOB: {dob} Journey State: {journeyState}
                            <button on:click={() => console.log(patientsRef.doc(id).delete())}>Delete<button/>
                        </li>
                    {/if}
                {/each}
            </ul>
        </div>
    </div>
{/if}



<style>

   .list-BD {
        width: 90%;
        height: 100%;
        position: fixed;
        background: rgba(0, 0, 0, 0.8);
   } 

    .list-modal {
        padding: 10px;
        border-radius: 10px;
        max-width: 90%;
        margin: 3% auto;
        text-align: center;
        background:  rgb(179, 102, 172);
        color: white;
        overflow-y: auto;
        height: 650px;
    }

    ul.no-bullets {
        list-style-type: none; /* Remove bullets */
        padding: 0; /* Remove padding */
        margin: 50px; /* Remove margins */
        text-align: left;
        color: white;
    }

</style>
