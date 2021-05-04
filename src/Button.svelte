<script>
    export let tecla;
    export let result;
    const error = "Error!";
    function handleClick() {
        switch (tecla) {
            case "CA":
                result = "";
                break;
            case "=":
                try {
                    result = eval(result);
                    result = String(result);
                } catch (e) {
                    result = error;
                }
                break;
            case "C":
                result = result.slice(0, -1);
                break;
            case "%":
                try {
                    result = Number(result) / 100;
                    result = String(result);
                } catch (e) {
                    result = error;
                }
                break;
            case "±" :
                try {
                    result = Number(result);
                    result = -result;
                    result = String(result);
                } catch (e) {
                    result = error;
                }
                break;
            case "√":
                try {
                    result = String(Math.sqrt(Number(result)));
                } catch (e) {
                   result = error;
                }
                break;
            case ".":
                if (!result.includes(".")) {
                    result = result !== "" ? result = result+"." : "0.";
                }
                break;
            case "x²":
                try {
                    result = Math.pow(result,2);
                } catch (e) {
                    result = error
                }
                break;
            default:
                result = result === error || result === "0" ? tecla : result + tecla;
                break;
        }
    }
</script>

<style>
    button {
        width: 100%;
        margin: 0.3em;
        border: 0;
        padding: 1em 0.5em;
        box-shadow: 0.1em -0.1em 0.2em #676767, -0.1em 0.1em 0.2em #656565;
        background: white;
        outline: none;
        font-size: 110%;
        cursor: pointer;
        border-radius: 0.2em;
        transition: box-shadow 0.4s;
    }
    button:hover {
        box-shadow: 0.1em -0.1em 0.2em transparent, -0.1em 0.1em 0.2em transparent,
        inset 0.1em -0.1em 0.3em 0.1em #fff, inset -0.1em 0.1em 0.4em #ccc;
    }

    #\\\= {
        background: #ff3e00;
        width: 100%;
        color: #ffffff;
    }
    #\\\=:hover {
        box-shadow: 0.1em -0.1em 0.2em transparent, -0.1em 0.1em 0.2em transparent,
        inset 0.1em -0.1em 0.3em 0.1em #ff3e00, inset -0.1em 0.1em 0.4em #73392d;
    }

    #\\0, #\\±, #\\\. {
        width: 25%;
    }

    #\\CA {
        background: darkblue;
        color: #ffffff;
    }

    #\\CA:hover {
        box-shadow: 0.1em -0.1em 0.2em transparent, -0.1em 0.1em 0.2em transparent,
        inset 0.1em -0.1em 0.3em 0.1em darkblue, inset -0.1em 0.1em 0.4em #220d35;
    }

    #\\C {
        background: darkslateblue;
        color: #ffffff;
    }

    #\\C:hover {
        box-shadow: 0.1em -0.1em 0.2em transparent, -0.1em 0.1em 0.2em transparent,
        inset 0.1em -0.1em 0.3em 0.1em darkslateblue, inset -0.1em 0.1em 0.4em #220d35;
    }

</style>

<button id="\{tecla}" on:click={handleClick}>{tecla}</button>