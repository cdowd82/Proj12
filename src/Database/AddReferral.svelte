<script>

    export let showNewRefModal = false;
    export let patientRef;
    import { fly } from 'svelte/transition';
    import { createEventDispatcher } from 'svelte';

    let dispatch = createEventDispatcher();

    let medicalHistory = "";
    let medications = "";
    let allergiesAndReactions = "";
    let socialStatus = "";
    let patientName = "";
    let firstName = '';
    let middleNames = '';
    let lastName = '';
    let age = ''
    let mrn = '';
    let refDr = "";
    let dob = "";
    let refDate = "";
    let refAdded = true;
    let isUrgent = false;
    let CarryPatient = false;
    let journeyState = 'W';
    
    const toggleShowNewRefModal = () => {
        dispatch('toggleShowNewRefModal', showNewRefModal);
    }

    async function addReferral() {
        patientName = firstName + ' ' + middleNames + ' ' + lastName;
        if (firstName == '' || lastName == '') {
            alert("No Name Entered");
        } else {
            await patientRef.add({
                                    medicalHistory,
                                    medications,
                                    allergiesAndReactions,
                                    socialStatus,
                                    firstName, 
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
            console.log(patientRef.id);
        }
    };

</script>



<div class="workupNewRefBD" in:fly="{{y: -1000, duration: 500}}" on:click|self>
    <div class="workupNewRefModal" >
        <h2>New Referral Details</h2>
        <form on:submit|preventDefault={addReferral}> 
            <hr>
            <label> Urgent? (tick for yes) </label>
            <input type="checkbox" bind:value={isUrgent}><br>
            <hr>
            <input type="text" placeholder="First Name" bind:value={firstName}><br>
            <input type="text" placeholder="Middle Names" bind:value={middleNames}><br>
            <input type="text" placeholder="Last Name" bind:value={lastName}><br>
            <input type="number" placeholder="MRN" bind:value={mrn}><br>
            <input type="number" placeholder="Age" bind:value={age}><br>
            <input type="text" placeholder="Referring Physician" bind:value={refDr}><br>
            <label> DOB </label>
                <input type="date" placeholder="DOB" bind:value={dob}>
            <br>
            <div>Ref Date</div>
            <input type="date" placeholder="Date of Referral" bind:value={refDate}><br>
            <br>
            <hr>
            <label> Medical History </label>
            <textarea class="medical-history" cols="30" rows="10" placeholder="Medical History" bind:value={medicalHistory}/>
                <label> Medications </label>
            <textarea class="medications" cols="30" rows="10" placeholder="Medications" bind:value={medications}/>
                <label> Allergies and Adverse Drung Reactions </label>
            <textarea class="allerges-and-reactions" cols="30" rows="10" 
                placeholder="Allergies and Adverse Drung Reactions" bind:value={allergiesAndReactions}/>
                <label> Social Status </label>
            <textarea class="social-status" cols="30" rows="10" placeholder="Social Status" bind:value={socialStatus}/>
                <label> Funcational Status </label>
            <textarea class="funcational-status" cols="30" rows="10" placeholder="Funcational Status"></textarea> 
            <hr>
            <label> Carry Patient? (tick for yes) </label>
                <input type="checkbox" bind:value={CarryPatient}><br>
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
        overflow-y: auto;
        height: 650px;
    }
    
</style>