<script>
    export let showNewRefModal = false;
</script>

{#if showNewRefModal}
    <div class="workupNewRefBD" on:click|self>
        <div class="workupNewRefModal">
            <p>Add Details </p>
            <hr>
            <form>
                <input type="text" placeholder="First Name"><br>
                <input type="text" placeholder="Middle Names"><br>
                <input type="text" placeholder="Last Name"><br>
                <input type="number" placeholder="MRN"><br>
                <input type="text" placeholder="Referring Dr"><br>
                <div>DOB </div><input type="date" placeholder="DOB"><br>
                <div>Ref Date </div><input type="date" placeholder="Date of Referral"><br>
                <br>
                <div>Urgent (Y/N)</div>
                <input type="checkbox" placeholder="Urgent (Y/N)">
                <hr>
                <button on:click>Add Patient</button>
            </form>
        </div>
    </div>
{/if}

<style>

    .workupNewRefBD {
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0, 0, 0, 0.8);
    }

    .workupNewRefModal {
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 3% auto;
        text-align: center;
        background:  rgb(179, 102, 172);
        color: white;
    }
    
</style>