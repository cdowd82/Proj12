<script>

    export let showNewRefModal = false;
    export let patientRef;
    import { fly } from 'svelte/transition';
    import { createEventDispatcher } from 'svelte';

    let dispatch = createEventDispatcher();

    let patientName = "";
    let firstName = '';
    let middleNames = '';
    let lastName = '';
    let mrn = '';
    let refDr = "";
    let dob = "";
    let refDate = "";
    let refAdded = true;
    let isUrgent = false;
    let journeyState = 'W';
    
    const toggleShowNewRefModal = () => {
        dispatch('toggleShowNewRefModal', showNewRefModal);
    }

    async function addReferral() {
        patientName = firstName + ' ' + middleNames + ' ' + lastName;
        await patientRef.add({firstName, 
                              middleNames, 
                              lastName, 
                              mrn, 
                              refDr, 
                              dob, 
                              refDate, 
                              patientName, 
                              dateAdded: Date.now(),
                              refAdded,
                              isUrgent,
                              journeyState,
                            });

        firstName = "";
        middleNames = "";
        lastName = "";
        mrn = "";
        refDr = "";
        dob = "";
        refDate = "";
        refAdded= false;
        toggleShowNewRefModal();

    };

</script>



<div class="workupNewRefBD" in:fly="{{y: -1000, duration: 500}}" on:click|self>
    <div class="workupNewRefModal" >
        <p>Add Details </p>
        <hr>
        <form on:submit|preventDefault={addReferral}>
            <input type="text" placeholder="First Name" bind:value={firstName}><br>
            <input type="text" placeholder="Middle Names" bind:value={middleNames}><br>
            <input type="text" placeholder="Last Name" bind:value={lastName}><br>
            <input type="number" placeholder="MRN" bind:value={mrn}><br>
            <input type="text" placeholder="Referring Physician" bind:value={refDr}><br>
            <label> DOB </label>
                <input type="date" placeholder="DOB" bind:value={dob}>
            <br>
            <div>Ref Date</div>
            <input type="date" placeholder="Date of Referral" bind:value={refDate}><br>
            <br>
            <div>Urgent (Y/N)</div>
            <input type="checkbox" placeholder="Urgent (Y/N)" bind:checked={isUrgent}>
            <hr>
            <button type="submit">Add Patient</button>
        </form>
    </div>
</div>



<style>

    .workupNewRefBD {
        width: 90%;
        height: 100%;
        position: fixed;
        background: rgba(0, 0, 0, 0.8);
    }

    .workupNewRefModal {
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 3% auto;
        text-align: center;
        background:  rgb(179, 102, 172);
        color: white;
    }
    
</style>