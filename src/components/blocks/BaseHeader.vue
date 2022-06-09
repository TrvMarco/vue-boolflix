<template>
  <header>  
        <div class="input-group mb-3">
            <input type="text" class="form-control" placeholder="Cerca un titolo" aria-label="Recipient's username" aria-describedby="button-addon2">
            <button class="btn btn-outline-secondary" type="button" id="button-addon2"><i class="fa-solid fa-magnifying-glass"></i></button>
        </div>
  </header>
</template>

<script>
export default {
    name: 'BaseHeader'
}
</script>

<style lang="scss" scoped>
    header{
        height: 5rem;
        background-color: #000;
        display: flex;
        justify-content: flex-end;
        .input-group{
            width: 20%;
            align-self: flex-end;
        }
    }
</style>