
<script>


    import { Collection , Doc } from 'sveltefire'
    import PatientListWorkup from '/Users/Chris/Projects/Proj12/src/Database/PatientListWorkup.svelte';
    
    let showWorkupList = false;

    let query = (ref) => ref.orderBy('lastName');

    const showPatientsList = () => {
        showWorkupList = !showWorkupList;
        console.log(showWorkupList);
    }

    function selectPatient() {
        alert("Patient Selected");
    }

    async function deletePatient() {
    }
     
</script>

    <Collection path={'patients/'} {query} let:data={patients} let:last let:ref={patientRef}>

        <!-- Render for workup -->
        <p on:click={showPatientsList}>View Workup Patients</p>
        
        {#if showWorkupList}
            <PatientListWorkup {patients} {patientRef}/> 
        {/if}

    </Collection>



<style>

</style>