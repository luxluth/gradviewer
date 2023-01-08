<script lang="ts">
import { code } from '$lib/Gradients'

let codeIsShow = true
let backdropActive = false
let expandGrad = false

function toogleExpand() {
    backdropActive = !backdropActive
    expandGrad = !expandGrad
    codeIsShow = !codeIsShow
}

</script>
<!-- div.gradCode that can be edited  and parse in the same time -->
<textarea class="gradCode {codeIsShow? "" : "unshow"}" bind:value={$code} rows="50"></textarea>
<div class="backdrop {backdropActive? "show" : ""}" on:click={() => toogleExpand()} on:keydown></div>
<div class="grad {expandGrad? "expand" : ""}" style="{$code}" on:click={() => toogleExpand()} on:keydown></div>

<style>
    .unshow {
        display: none;
    }
    .backdrop {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        z-index: 100;
        display: none;
        transition: all 0.3s ease-in-out;
    }
    .backdrop.show {
        display: block;
    }

    .expand {
        position: absolute;
        width: 80vw;
        height: 90vh;
        z-index: 150;
    }
</style>
