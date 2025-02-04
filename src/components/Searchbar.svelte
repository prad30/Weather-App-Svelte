
<script>
    import { createEventDispatcher } from "svelte";

    let city = "";
    const dispatch= createEventDispatcher();

    const search = () => {
        if (city !== "") {
            dispatch("search", city);
        } else {
            alert("Please enter a city name.");
        }
    };
</script>

<main>
    <div class="search-Container">
        <input
            type="text"
            class="input-city"
            placeholder="Enter City"
            bind:value={city}
            on:keydown={(e) => e.key === "Enter" && search()}
        />
        <img
            class="search-btn"
            src="/assets/search-icon.png"
            alt="search"
            on:keydown={search}
        />
    </div>
</main>

<style>
    .search-Container {
        position: absolute;
        width: 80%;
        top: 15%;
        left: 10%;
        display: flex;
        align-items: center;
    }

    .search-Container input {
        width: 100%;
        height: 50px;
        padding: 10px 20px;
        font-size: 18px;
        border-radius: 20px;
        border: 2px solid gray;
        outline: none;
    }

    .search-Container img {
        position: absolute;
        right: 15px;
        width: 30px;
        cursor: pointer;
    }
</style>
