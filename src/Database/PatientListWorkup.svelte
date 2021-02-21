<script>
    
    import { fly } from 'svelte/transition';

    import { createEventDispatcher }from 'svelte';
    let dispatch = createEventDispatcher(); 

    export let patients;
    export let patientsRef;
    export let showWorkupPatientList = false;
    export let showWorkupPatient = false;
    
    const showPatientWorkup = (id) => {
        let selected = [];
        let selectedPatientId = id;
        showWorkupPatient = true;
        selected[0] = selectedPatientId;
        selected[1] = showWorkupPatient;
        dispatch('showPatient', selected);
    };
    
</script>


<div>
    {#if showWorkupPatientList}
        <div class="list-BD" in:fly="{{x: -1000, duration: 500}}" on:click|self>
            <div class="list-modal">
                <ul class="no-bullets">
                    {#each patients as { patientName, dob, journeyState, firstName, lastName, id}, i}
                        {#if ((journeyState == 'W') && (firstName != "") && (lastName != ""))}
                            <li>
                                <div class="item">
                                    <div class="patient-name" on:click={ () => {showPatientWorkup(id)}}>
                                        {patientName} DOB: {dob} Journey State: {journeyState}
                                    </div>
                                    <!--
                                    <div class="patient-name" on:click={ () => (selectedPatientId = id)} 
                                            on:click={ () => console.log(selectedPatientId)}>
                                        {patientName} DOB: {dob} Journey State: {journeyState}
                                    </div>
                                    -->
                                    <div class="delete-btn">
                                        <button on:click|self={() => {
                                            if (confirm("Confirm Delete")) { 
                                                patientsRef.doc(id).delete();
                                            }
                                        }}>Delete
                                        <button/>
                                </div>
                                <div class="carry-patient">
                                        <label for="carry-patient">Carry Patient</label>
                                        <input type="checkbox">
                                    </div>
                                </div>
                            </li>
                        {/if}
                    {/each}
                </ul>
            </div>
        </div>
    {/if}
</div>



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
        overflow-y: auto;
    }

    .item {
        display: flex;
    }

    .patient-name {
        flex: 2;
    }

    .delete-btn {
        flex:1;   
    }

    .carry-patient {
        flex:1;
    }

</style>
