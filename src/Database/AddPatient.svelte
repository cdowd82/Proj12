<script>
    export let patientRef;
    let patientName = '';
    async function addPatient() {
        await patientRef.add({patientName, date: Date.now()});
        patientName = "";
    };
</script>



<form on:submit|preventDefault={addPatient}>
    <div>
        <input type="text" class="input" bind:value={patientName} placeholder="Patient Name">
    </div>
    <div>
        <button>Add Patient</button>
    </div>
</form>



<style>
    
</style>