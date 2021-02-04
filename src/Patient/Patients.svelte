<script lang="ts">

    import Patient from '/Users/Chris/Projects/Proj12/src/Patient/Patient.svelte';
    //import type { db } from '/Users/Chris/Projects/Proj12/src/App.svelte';

    /*
    db.collection('patients').onSnapshot( data => {
        
    });
    */

    let patients = [];
</script>

<div id="patients">
    {#each patients as patient}
        <div>user</div> 
    {/each}
</div>

<style></style>