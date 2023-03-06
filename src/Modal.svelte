<script>
    export let showModal = true;
    // export let message = 'default value';
    export let isPromo = false;
</script>

{#if showModal}
<div class="backdrop" class:promo={isPromo} on:click|self on:keyup> <!-- Event Forwarding -->
    <div class="modal">
        <!-- <slot name="title"></slot> Named slot-->
        <slot></slot>
    </div>
</div>
{/if}

<style>
.backdrop {
    height: 100%;
    width: 100%;
    position: fixed;
    background: rgba(0,0,0,0.8);
}
.modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: white;
}
.promo .modal {
    background: crimson;
    color: white;
}
</style>