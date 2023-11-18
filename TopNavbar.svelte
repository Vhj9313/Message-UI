<script>
    import Icon from "@iconify/svelte";

    let showOptions = false;

    function toggleOptions() {
        showOptions = !showOptions;
    }

    function handleOptionClick(option) {
        if (option === "copy") {
            console.log("Copy clicked");
        } else if (option === "delete") {
            console.log("Delete clicked");
        }
    }
</script>

<main>
    <div class="navbar">
        <div class="left">
            <Icon
                icon="ion:arrow-back-outline"
                color="black"
                width="25"
                height="25"
            />
        </div>

        <div
            class="options"
            on:click|stopPropagation={toggleOptions}
            on:keypress
        >
            {#if showOptions}
                <div
                    class="option"
                    on:click|stopPropagation={() => handleOptionClick("copy")}
                    on:keypress
                >
                    <Icon
                        icon="ion:copy"
                        color="black"
                        width="20"
                        height="20"
                    />
                </div>
                <div
                    class="option"
                    on:click|stopPropagation={() => handleOptionClick("delete")}
                    on:keypress
                >
                    <Icon
                        icon="fluent:delete-32-filled"
                        color="black"
                        width="20"
                        height="20"
                    />
                </div>
            {/if}
        </div>

        <div class="messages">Messages</div>

        <div
            on:click|stopPropagation={toggleOptions}
            on:keypress
            class="toggle"
        >
            <Icon
                icon="bi:three-dots-vertical"
                color="black"
                width="20"
                height="20"
            />
        </div>
    </div>
</main>

<style>
    .navbar {
        display: flex;
        align-items: center;
        justify-content: space-between;
        background-color: #f0f0f0;
    }

    .options {
        position: absolute;
        right: 10px;
        display: flex;
        flex-direction: row;
        margin-right: 40px;
    }

    .option,
    .toggle,
    .left {
        padding: 8px 10px;
        cursor: pointer;
    }

    .option:hover,
    .toggle:hover,
    .left:hover {
        background-color: #e0e0e0;
    }

    .messages {
        font-size: 20px;
        font-weight: bold;
    }

    @media (max-width: 768px) {
        .navbar {
            flex-direction: row;
        }

        .options {
            position: absolute;
            margin-right: 32px;
        }

        .option,
        .toggle,
        .left {
            padding: 4px 6px;
            cursor: pointer;
        }

        .messages {
            font-size: 16px;
            font-weight: bold;
        }
    }
</style>
