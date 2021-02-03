<script>
    import { fade, fly } from 'svelte/transition';

    function search() {
        alert("Search selected");
    }
    
</script>
 
<div class="search" out:fade="{{duration: 1}}">
    <div class="search-box" in:fade="{{duration: 2500}}" on:click={search}>
        <div class="search">
            <p>Search</p>
        </div>
    </div>
</div>

<style>

    .search {
        color: rgb(255, 255, 255);
        font-family: "Helvetica Neue", "Helvetica", "Arial", sans-serif;
    }

    @media(min-width:468px){
        .search {
            display:flex;  
            text-align: center;
            justify-content:space-between;
        }
    }

    .search-box {
        display: flex;
        justify-content: center;
        align-items: center;
        flex:1;
        order: 1;
        background-color: rgb(172, 63, 163);
        font-size: 25px;
    }

    .search .search-box:hover {
        background-color: rgb(179, 102, 172);
    }
    
</style>
