<script>
    import { fade, fly } from 'svelte/transition';
</script>

<div class="footer" transition:fly="{{y: -1000, duration: 1200}}"></div>

<style>
        /** Footer **/
        .footer {
        display: grid;
        grid-template-columns: auto;
        grid-template-rows: 50px;
        background-color: rgba(0, 0, 0, 0.8);
        color: rgba(0, 0, 0, 0.8);

    }
    
</style>