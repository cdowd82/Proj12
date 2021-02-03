<script>
    let newRefModal = true;

    function newRef() {
        newRefModal = !newRefModal;
        console.log(newRefModal)
    };
</script>

<div class="workupNewRef" on:click={newRef}>
    <div class="workupNewRefModal">
        <p>New Referral</p>
    </div>
</div>

<style>
    
</style>