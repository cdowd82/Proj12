
<script>

    import { Collection } from 'sveltefire'
    import PatientListWorkup from '/Users/Chris/Projects/Proj12/src/Database/PatientListWorkup.svelte';

    import { createEventDispatcher }from 'svelte';

    let dispatch = createEventDispatcher(); 
    
    let showWorkupPatientList = false;
    let showWorkupPatient = false;

    let query = (ref) => ref.orderBy('lastName');

    const showWorkupPatientsList = () => {
        showWorkupPatientList = !showWorkupPatientList;
        dispatch("showWorkupPatientList", showWorkupPatientList);
    }

    const showPatient = (e) => {
        let selected = e.detail;
        console.log(selected[0]);
        console.log(selected[1]);
    }

</script>



<Collection path={'patients/'} {query} let:data={patients} let:ref={patientsRef} let:last >
        
    <!-- Render for workup -->
    {#if !showWorkupPatientList}
        <p on:click={showWorkupPatientsList}>View Workup Patients</p>
    {/if}
        
    {#if showWorkupPatientList}
        <PatientListWorkup {patients} {patientsRef} {showWorkupPatientList} 
            {showWorkupPatient} on:click={showWorkupPatientsList} on:showPatient={showPatient}/>
    {/if}

</Collection>



<style>

</style>