<script>

    // Imports
    import Router from 'svelte-hash-router'
    import { fade, fly } from 'svelte/transition';
    import WorkupPage from '/Users/Chris/Projects/Proj12/src/Pages/WorkupPage.svelte';

    // Nav logic variables initial states 
    let showHome = true;
    let showWorkup = false;
    let showSearch = false;
    let showEval = false;
    let showProce = false;
    let showComp = false;

    // Navigation functions
    const enterWorkup = () => {
        showWorkup = true;
        showHome = false;
        showSearch = false;
        showEval = false;
        showProce = false;
        showComp = false;

    };

    const enterHome = () => {
        showWorkup = false;
        showHome = true;
        showSearch = false;
        showEval = false;
        showProce = false;
        showComp = false;
    }

    const enterSearch = () => {
        showWorkup = false;
        showHome = false;
        showSearch = true;
        showEval = false;
        showProce = false;
        showComp = false;
    };

    const enterEval = () => {
        showWorkup = false;
        showHome = false;
        showSearch = false;
        showEval = true;
        showProce = false;
        showComp = false;
    }

    const enterProce = () => {
        showWorkup = false;
        showHome = false;
        showSearch = false;
        showEval = false;
        showProce = true;
        showComp = false;
    }

    const enterComp = () => {
        showWorkup = false;
        showHome = false;
        showSearch = false;
        showEval = false;
        showProce = false;
        showComp = true;
    }

</script>

<div>

    <!-- HOMEPAGE -->
    {#if showHome}
        <div class="home-content" out:fade="{{duration: 1}}">
            <div class="search-box" in:fade="{{duration: 1600}}" on:click={enterSearch}>
                <p>Search</p>
            </div>
            <div class="workup-box" in:fade="{{duration: 1300}}" on:click={enterWorkup}>
                <p>Workup</p>
            </div>
            <div class="evaluation-box" in:fade="{{duration: 1000}}" on:click={enterEval}>
                <p>Evaluation</p>
            </div>
            <div class="complete-box" in:fade="{{duration: 800}}" on:click={enterComp}>
                <p>Complete</p>
            </div>     
            <div class="procedure-box" in:fade="{{duration: 500}}" on:click={enterProce}>
                <p>Procedure</p>
            </div>
        </div>
    {/if}

    <!-- WORKUP -->
    {#if showWorkup}
    <div class="workup-content" >
        <div class="workup-w-box" in:fade="{{duration: 1000}}" >
            <p>Workup</p>
            <WorkupPage/>
        </div>
        <div class="workup-h-box" in:fade="{{duration: 300}}" on:click={enterHome}>
            <p>H</p>
        </div>
        <div class="workup-s-box" in:fly="{{y: 700, x: -700, duration: 500}}" on:click={enterSearch}>
            <p>S</p>
        </div>
        <div class="workup-e-box" in:fly="{{y: 700, x: -700, duration: 800}}" on:click={enterEval}>
            <p>E</p>
        </div>
        <div class="workup-p-box" in:fly="{{y: 700, x: -700, duration: 1100}}" on:click={enterProce}>
            <p>P</p>
        </div>
        <div class="workup-c-box" in:fly="{{y: 700, x: -700, duration: 1300}}" on:click="{enterComp}">
            <p>C</p>
        </div>
    </div>
    {/if}

    <!-- SHOWSEARCH -->
    {#if showSearch}
    <div class="search-content" out:fade="{{duration: 1}}">
        <div class="search-s-box" in:fade="{{duration: 2500}}">
            <div class="search">
                <p>Search</p>
            </div>
        </div>
        <div class="search-h-box" in:fade="{{duration: 300}}" on:click={enterHome}>
            <p>H</p>
        </div>
        <div class="search-w-box" in:fly="{{y: 700, x: -700, duration: 500}}" on:click={enterWorkup}>
            <p>W</p>
        </div>
        <div class="search-e-box" in:fly="{{y: 700, x: -700, duration: 800}}" on:click={enterEval}>
            <p>E</p>
        </div>
        <div class="search-p-box" in:fly="{{y: 700, x: -700, duration: 1100}}" on:click={enterProce}>
            <p>P</p>
        </div>
        <div class="search-c-box" in:fly="{{y: 700, x: -700, duration: 1300}}" on:click={enterComp}>
            <p>C</p>
        </div>
    </div>
    {/if}

    <!-- EVALUATION -->
    {#if showEval}
    <div class="eval-content" out:fade="{{duration: 1}}">
        <div class="eval-e-box" in:fade="{{duration: 2500}}">
            <div class="evaluation">
                <p>Evaluation</p>
            </div>
        </div>
        <div class="eval-h-box" in:fade="{{duration: 300}}" on:click={enterHome}>
            <p>H</p>
        </div>
        <div class="eval-w-box" in:fly="{{y: 700, x: -700, duration: 500}}" on:click={enterWorkup}>
            <p>W</p>
        </div>
        <div class="eval-s-box" in:fly="{{y: 700, x: -700, duration: 800}}" on:click={enterSearch}>
            <p>E</p>
        </div>
        <div class="eval-p-box" in:fly="{{y: 700, x: -700, duration: 1100}}" on:click={enterProce}>
            <p>P</p>
        </div>
        <div class="eval-c-box" in:fly="{{y: 700, x: -700, duration: 1300}}" on:click={enterComp}>
            <p>C</p>
        </div>
    </div>
    {/if}

    <!-- PROCEDURE -->
    {#if showProce}
    <div class="proce-content" out:fade="{{duration: 1}}">
        <div class="proce-p-box" in:fade="{{duration: 2500}}">
            <div class="Procedure">
                <p>Procedure</p>
            </div>
        </div>
        <div class="proce-h-box" in:fade="{{duration: 300}}" on:click={enterHome}>
            <p>H</p>
        </div>
        <div class="proce-w-box" in:fly="{{y: 700, x: -700, duration: 500}}" on:click={enterWorkup}>
            <p>W</p>
        </div>
        <div class="proce-s-box" in:fly="{{y: 700, x: -700, duration: 800}}" on:click={enterSearch}>
            <p>S</p>
        </div>
        <div class="proce-e-box" in:fly="{{y: 700, x: -700, duration: 1100}}" on:click={enterEval}>
            <p>E</p>
        </div>
        <div class="proce-c-box" in:fly="{{y: 700, x: -700, duration: 1300}}" on:click={enterComp}>
            <p>C</p>
        </div>
    </div>
    {/if}

        <!-- COMPLETE -->
    {#if showComp}
        <div class="comp-content" out:fade="{{duration: 1}}">
            <div class="comp-c-box" in:fade="{{duration: 2500}}">
                <div class="Complete">
                    <p>Complete</p>
                </div>
            </div>
            <div class="comp-h-box" in:fade="{{duration: 300}}" on:click={enterHome}>
                <p>H</p>
            </div>
            <div class="comp-w-box" in:fly="{{y: 700, x: -700, duration: 500}}" on:click={enterWorkup}>
                <p>W</p>
            </div>
            <div class="comp-s-box" in:fly="{{y: 700, x: -700, duration: 800}}" on:click={enterSearch}>
                <p>S</p>
            </div>
            <div class="comp-e-box" in:fly="{{y: 700, x: -700, duration: 1100}}" on:click={enterEval}>
                <p>E</p>
            </div>
            <div class="comp-p-box" in:fly="{{y: 700, x: -700, duration: 1300}}" on:click={enterProce}>
                <p>P</p>
            </div>
        </div>
    {/if}

</div>

<main>
</main>

<style>

    /*** HOME PAGE ***/
    .home-content {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 50px 320px 320px;
    }

    .search-box {
        grid-column-start: 1;
        grid-column-end: 3;
        background-color: rgb(172, 63, 163);
        color: white;
        justify-content: center;
        align-content: center;
    }

    .home-content .search-box:hover {
        background-color: rgb(179, 102, 172);
    }

    .workup-box {
        grid-column-start: 1;
        grid-column-end: 1;
        grid-row-start: 2;
        grid-row-end: 2;
        color: rgb(255, 255, 255);
        background-color: rgb(253, 86, 86);
        font-size: 75px
    }

    .home-content .workup-box:hover {
        background-color: rgb(253, 128, 128);
    }

    .evaluation-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 2;
        grid-row-end: 2;
        color:rgb(255, 255, 255);
        background-color: rgb(255, 197, 72);
        font-size: 75px
    }

    .home-content .evaluation-box:hover {
        background-color: rgb(255, 215, 129);
    }

    .procedure-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 3;
        grid-row-end: 3;
        color:rgb(255, 255, 255);
        background-color: rgb(60, 196, 89);
        font-size: 75px
    }

    .home-content .procedure-box:hover {
        background-color: rgb(118, 202, 137);
    }

    .complete-box {
        grid-column-start: 1;
        grid-column-end: 1;
        grid-row-start: 3;
        grid-row-end: 3;
        color:rgb(255, 255, 255);
        background-color:  rgb(59, 76, 235);
        font-size: 75px
    }

    .home-content .complete-box:hover {
        background-color: rgb(101, 114, 238);
    }

    .content > div {
        border-color: rgba(0, 0, 0, 10);;
        border-bottom: 2px solid black;
        border-right: 1px solid black;
        border-left: 1px solid black;
    }

    /*** WORKUP PAGE ***/
    .workup-content {
        display: grid;
        grid-template-columns: 10fr 1fr;
        grid-template-rows:  135px 135px 135px 135px 135px;
    }

    .workup-h-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 1;
        grid-row-end: 2;
        background: rgba(63, 62, 62, 0.986);
        color: rgb(255, 255, 255);
    }

    .workup-content .workup-h-box:hover {
        background-color: rgba(109, 109, 109, 0.986);
    }

    .workup-w-box {
        grid-column-start: 1;
        grid-column-end: 1;
        grid-row-start: 1;
        grid-row-end: 6;
        background: rgb(156, 100, 100);
        color: rgb(255, 255, 255);
    }

    .workup-s-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 2;
        grid-row-end: 2;
        background-color: rgb(172, 63, 163);
        color: white;
    }

    .workup-content .workup-s-box:hover {
        background-color: rgb(179, 102, 172);
    }

    .workup-e-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 3;
        grid-row-end: 3;
        background:  rgb(255, 197, 72);
        color: white;
    }

    .workup-content .workup-e-box:hover {
        background-color: rgb(255, 215, 129);
    }

    .workup-p-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 4;
        grid-row-end: 4;
        color:rgb(255, 255, 255);
        background-color: rgb(60, 196, 89);
    }

    .workup-content .workup-p-box:hover {
        background-color: rgb(118, 202, 137);
    }

    .workup-c-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 5;
        grid-row-end: 5;
        color:rgb(255, 255, 255);
        background-color:  rgb(59, 76, 235);
    }

    .workup-content .workup-c-box:hover {
        background-color: rgb(101, 114, 238);
    }

    /*** Search ***/
    .search-content {
        display: grid;
        grid-template-columns: 10fr 1fr;
        grid-template-rows:  135px 135px 135px 135px 135px;
    }

    .search-s-box {
        grid-column-start: 1;
        grid-column-end: 1;
        grid-row-start: 1;
        grid-row-end: 6;
        background-color: rgb(172, 63, 163);
        color: rgb(255, 255, 255);
    }

    .search-h-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 1;
        grid-row-end: 2;
        background: rgba(63, 62, 62, 0.986);
        color: rgb(255, 255, 255);
    }

    .search-content .search-h-box:hover {
        background-color: rgba(109, 109, 109, 0.986);
    }

    .search-w-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 2;
        grid-row-end: 3;
        background-color: rgb(253, 86, 86);
        color: rgb(255, 255, 255);
    }

    .search-content .search-w-box:hover {
        background-color: rgb(253, 128, 128);
    }

    .search-e-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 3;
        grid-row-end: 4;
        background:  rgb(255, 197, 72);
        color: rgb(255, 255, 255);
    }

    .search-content .search-e-box:hover {
        background-color: rgb(255, 215, 129);
    }

    .search-p-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 4;
        grid-row-end: 5;
        background-color: rgb(60, 196, 89);
        color: rgb(255, 255, 255);
    }

    .search-content .search-p-box:hover {
        background-color: rgb(118, 202, 137);
    }

    .search-c-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 5;
        grid-row-end: 6;
        color:rgb(255, 255, 255);
        background-color:  rgb(59, 76, 235);
    }

    .search-content .search-c-box:hover {
        background-color: rgb(101, 114, 238);
    }

    /*** EVALUATION ***/
    .eval-content {
        display: grid;
        grid-template-columns: 10fr 1fr;
        grid-template-rows:  135px 135px 135px 135px 135px;
    }

    .eval-e-box {
        grid-column-start: 1;
        grid-column-end: 1;
        grid-row-start: 1;
        grid-row-end: 6;
        background:  rgb(255, 197, 72);
        color: rgb(255, 255, 255);
    }

    .eval-h-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 1;
        grid-row-end: 2;
        background: rgba(63, 62, 62, 0.986);
        color: rgb(255, 255, 255);
    }

    .eval-content .eval-h-box:hover {
        background-color: rgba(109, 109, 109, 0.986);
    }

    .eval-s-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 2;
        grid-row-end: 3;
        background-color: rgb(172, 63, 163);
        color: rgb(255, 255, 255);
    }

    .eval-content .eval-s-box:hover {
        background-color: rgb(179, 102, 172);
    }

    .eval-w-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 3;
        grid-row-end: 4;
        background-color: rgb(253, 86, 86);
        color: rgb(255, 255, 255);
    }

    .eval-content .eval-w-box:hover {
        background-color: rgb(253, 128, 128);
    }

    .eval-p-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 4;
        grid-row-end: 5;
        background-color: rgb(60, 196, 89);
        color: rgb(255, 255, 255);
    }

    .eval-content .eval-p-box:hover {
        background-color: rgb(118, 202, 137);
    }

    .eval-c-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 5;
        grid-row-end: 6;
        color:rgb(255, 255, 255);
        background-color:  rgb(59, 76, 235);
    }

    .eval-content .eval-c-box:hover {
        background-color: rgb(101, 114, 238);
    }

    /*** Procedure ***/
    .proce-content {
        display: grid;
        grid-template-columns: 10fr 1fr;
        grid-template-rows:  135px 135px 135px 135px 135px;
    }

    .proce-p-box {
        grid-column-start: 1;
        grid-column-end: 1;
        grid-row-start: 1;
        grid-row-end: 6;
        background-color: rgb(60, 196, 89);
        color: rgb(255, 255, 255);
    }

    .proce-h-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 1;
        grid-row-end: 2;
        background: rgba(63, 62, 62, 0.986);
        color: rgb(255, 255, 255);
    }

    .proce-content .proce-h-box:hover {
        background-color: rgba(109, 109, 109, 0.986);
    }

    .proce-s-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 2;
        grid-row-end: 3;
        background-color: rgb(172, 63, 163);
        color: rgb(255, 255, 255);
    }

    .proce-content .proce-s-box:hover {
        background-color: rgb(179, 102, 172);
    }

    .proce-w-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 3;
        grid-row-end: 4;
        background-color: rgb(253, 86, 86);
        color: rgb(255, 255, 255);
    }

    .proce-content .proce-w-box:hover {
        background-color: rgb(253, 128, 128);
    }

    .proce-e-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 4;
        grid-row-end: 5;
        background:  rgb(255, 197, 72);
        color: rgb(255, 255, 255);
    }

    .proce-content .proce-e-box:hover {
        background-color: rgb(255, 215, 129);
    }

    .proce-c-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 5;
        grid-row-end: 6;
        color:rgb(255, 255, 255);
        background-color:  rgb(59, 76, 235);
    }

    .proce-content .proce-c-box:hover {
        background-color: rgb(101, 114, 238);
    }

    /*** Complete ***/
    .comp-content {
        display: grid;
        grid-template-columns: 10fr 1fr;
        grid-template-rows:  135px 135px 135px 135px 135px;
    }

    .comp-c-box {
        grid-column-start: 1;
        grid-column-end: 1;
        grid-row-start: 1;
        grid-row-end: 6;
        background-color:  rgb(59, 76, 235);
        color: rgb(255, 255, 255);
    }

    .comp-h-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 1;
        grid-row-end: 2;
        background: rgba(63, 62, 62, 0.986);
        color: rgb(255, 255, 255);
    }

    .comp-content .comp-h-box:hover {
        background-color: rgba(109, 109, 109, 0.986);
    }

    .comp-s-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 2;
        grid-row-end: 3;
        background-color: rgb(172, 63, 163);
        color: rgb(255, 255, 255);
    }

    .comp-content .comp-s-box:hover {
        background-color: rgb(179, 102, 172);
    }

    .comp-w-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 3;
        grid-row-end: 4;
        background-color: rgb(253, 86, 86);
        color: rgb(255, 255, 255);
    }

    .comp-content .comp-w-box:hover {
        background-color: rgb(253, 128, 128);
    }

    .comp-e-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 4;
        grid-row-end: 5;
        background:  rgb(255, 197, 72);
        color: rgb(255, 255, 255);
    }

    .comp-content .comp-e-box:hover {
        background-color: rgb(255, 215, 129);
    }

    .comp-p-box {
        grid-column-start: 2;
        grid-column-end: 2;
        grid-row-start: 5;
        grid-row-end: 6;
        color:rgb(255, 255, 255);
        background-color: rgb(60, 196, 89);
    }

    .comp-content .comp-p-box:hover {
        background-color: rgb(118, 202, 137);
    }


</style>

<Router/>
