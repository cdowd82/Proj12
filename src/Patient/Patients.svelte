<script lang="ts">

    import Patient from '/Users/Chris/Projects/Proj12/src/Patient/Patient.svelte';
    //import { db } from '/Users/Chris/Projects/Proj12/src/App.svelte';

    let patients = [];

    /*
    db.collection('patients').onSnapshot( data => {
        patients = data.docs
    })
    */

</script>

<div id="patients">
    {#each patients as patient}
        <div>user</div> 
    {/each}
</div>

<style></style>