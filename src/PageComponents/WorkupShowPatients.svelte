
<script>

    import { Collection } from 'sveltefire'
    import PatientListWorkup from '/Users/Chris/Projects/Proj12/src/Database/PatientListWorkup.svelte';
    import WorkupShowPatientData from '/Users/Chris/Projects/Proj12/src/Modals/WorkupShowPatientData.svelte';

    import { createEventDispatcher }from 'svelte';

    let dispatch = createEventDispatcher(); 
    
    let showWorkupPatientList = false;
    let showWorkupPatient = false;
    let selected;

    let query = (ref) => ref.orderBy('lastName');

    const showWorkupPatientsList = () => {
        showWorkupPatientList = !showWorkupPatientList;
        dispatch("showWorkupPatientList", showWorkupPatientList);
    }

    const showPatient = (e) => {
        selected = e.detail;
        console.log(selected[0]);
        console.log(selected[1]);
        showWorkupPatientList = false;
        showWorkupPatient = selected[1];
    }

    const toggle = () => {
        showWorkupPatient  = false;
        showWorkupPatientList = true;
    }

</script>



<Collection path={'patients/'} {query} let:data={patients} let:ref={patientsRef}>
        
    <!-- Render for workup -->
    {#if !showWorkupPatientList && !showWorkupPatient}
        <p on:click={showWorkupPatientsList}>View Workup Patients</p>
    {/if}
        
    {#if showWorkupPatientList}
        <PatientListWorkup {patients} {patientsRef} {showWorkupPatientList} 
            {showWorkupPatient} on:click={showWorkupPatientsList} on:showPatient={showPatient}/>
    {/if}

    {#if showWorkupPatient}
        <WorkupShowPatientData {selected} on:click={toggle}/>
    {/if}

</Collection>



<style>

</style>