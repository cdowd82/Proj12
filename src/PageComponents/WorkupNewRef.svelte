<script>

    import WorkupNewRefModal from '/Users/Chris/Projects/Proj12/src/Modals/WorkupNewRefModal.svelte';
    import { createEventDispatcher }from 'svelte';

    let dispatch = createEventDispatcher(); 

    const showNewRefModal = (e) => {
        dispatch("showNewRefModal", e.detail);
    }

</script>



<div class="new-ref-modal">
    <WorkupNewRefModal on:showNewRefModal={showNewRefModal}/>
</div>



<style>

    .new-ref-modal {
        height: 100%;
        width: 100%;
    }

</style>
