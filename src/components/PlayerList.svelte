<script>
    let players_promise = getPlayers();

    async function getPlayers() {
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer testingthis");
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Access-Control-Allow-Origin", "*")
    
        var raw = "%playerlist_all:_list%";
    
        var requestOptions = {
            method: "POST",
            headers: myHeaders,
            body: raw,
        };
    
        var response = await fetch(
            "http://craft.divnectar.com:4444/api/placeholder",
            requestOptions
        );
        var res_json = await response.json();
        var players = res_json.placeholder.split(", ");
        console.log(players)
        return players
    }
    </script>

<div
    class="block min-w-[200px] p-6 m-6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
>
    <h5
        class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white"
    >
        Players Online:
    </h5>
    <ol>
    {#await players_promise}
        <p>...fetching data</p>
    {:then p}
        {#each Object.entries(p) as [player]}
            <li>{player}</li>
        {/each}
    {:catch error}
        <p style="color: red">{error.message}</p>
    {/await}
    </ol>
</div>


