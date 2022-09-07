<script>
export let persons = []
let search = "";
$: filteredList = persons.filter(item => item.name.indexOf(search) !== -1);


</script>
<div class="container">
    <div class="filter">
        <img class="icon" src="https://static.thenounproject.com/png/101791-200.png" alt="">
        <input bind:value={search} type="search" placeholder="Search for a user">

    </div>
    {#each filteredList as person, index}
        <div class="content">
            <img src={person.cover} alt="">
            <p>{person.name}</p>
        </div>
    {/each}
</div>

<style>
.container {
    width: 20vw;
    /* height: 40vh; */
    background-color: #F2F2F2;
    padding: 2em;
    border-radius: 24px;
    /* display: flex; */

}
.content {
    margin-top: 30px;
    display: flex;
    justify-items: center;
    align-items: center;
    color: #BCBCBC;

}

.filter {
    position: relative;

}

input {
        width: 100%;
        height: 45px;
        border-radius: 15px;
        background-color: #DBEBE3;
        text-decoration: none;
        border: 0px;
        padding-left: 25px;
        text-indent: 40px;

}
img {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    object-fit: fill;
    margin-right: 2em;
}

.icon {
    position: absolute;
    width: 30px;
    height: 30px;
    top: 50%;
    left: 10%;
    transform: translate(-50%, -50%);  overflow: hidden;

}

</style>