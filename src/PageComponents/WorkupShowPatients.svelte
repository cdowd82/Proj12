
<script>

    import { Collection } from 'sveltefire'
    import PatientListWorkup from '/Users/Chris/Projects/Proj12/src/Database/PatientListWorkup.svelte';
    
    let showWorkupPatientList = false;

    let query = (ref) => ref.orderBy('lastName');

    const showWorkupPatientsList = () => {
        showWorkupPatientList = !showWorkupPatientList;
        console.log(showWorkupPatientList);
    }



</script>



    <Collection path={'patients/'} {query} let:data={patients} let:ref={patientsRef} let:last >
        
        <!-- Render for workup -->
        <p on:click={showWorkupPatientsList}>View Workup Patients</p>
        
        {#if showWorkupPatientList}
            <PatientListWorkup {patients} {patientsRef} {showWorkupPatientList} on:click={showWorkupPatientsList}/>
        {/if}

    </Collection>

<style>

</style>