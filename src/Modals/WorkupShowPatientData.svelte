<script>

    import { fly } from 'svelte/transition';
    import { Collection} from 'sveltefire'

    export let selected;
    let patientId = selected[0];

</script>

<div class="show-patient-BD" in:fly="{{x: 1000, duration: 500}}" on:click|self>
    <div class="show-patient-modal">
        <h2>Workup Details</h2>
        <hr>

        <Collection path={'patients/'} let:data={patients} let:ref={patientsRef}>
            {#each patients as { patientName, dob, journeyState, mrn, age, refDr, id, refDate,
                medicalHistory, allergiesAndReactions, medications, socialStatus, funcStatus, firstName}}
                {#if patientId == id}
                    <p>{patientName}</p>
                    <hr>
                    <p>First Name: {firstName}</p>
                    <p>Patient ID:  {patientId}</p>
                    <p>DOB: {dob}</p>
                    <p>Journey State: {journeyState}</p>
                    <p>MRN: {mrn}</p>
                    <p>Age: {age}</p>
                    <p>Referring Dr: {refDr}</p>
                    <p>Referral Date: {refDate}</p>
                    <hr>
                    <p>Medical History: {medicalHistory}</p>
                    <p>Medications: {medications}</p>
                    <p>Allergies and Adverse Drug Reactions: {allergiesAndReactions}</p>
                    <p>Social Status: {socialStatus}</p>
                    <p>Functional Status: {funcStatus}</p>
                {/if}
            {/each}


        </Collection>
    </div>
</div>>


<style>

.show-patient-BD {
        width: 90%;
        height: 100%;
        position: fixed;
        background: rgba(0, 0, 0, 0.8);
}

.show-patient-modal {
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