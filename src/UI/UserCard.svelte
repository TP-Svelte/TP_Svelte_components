<script>
export let persons = []
export let darkMode;

let search = "";
$: filteredList = persons.filter(item => item.name.indexOf(search) !== -1);


</script>
<div class={darkMode ?  'container' : 'container-dark'}>
    <div class="filter">
        <img class="icon" src="https://static.thenounproject.com/png/101791-200.png" alt="">
        <input class={darkMode ?  'input-light' : 'input-dark'} bind:value={search} type="search" placeholder="Search for a user">

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
    margin: 2em;
    width: 20vw;
    max-width: 20vw;
    background-color: #F2F2F2;
    padding: 2em;
    border-radius: 24px;
            transition: 0.3s all ease-in-out;

}
.container-dark {
    margin: 2em;
    width: 20vw;
    background-color: #001014;
    padding: 2em;
    border-radius: 24px;
    transition: 0.3s all ease-in-out;

}

.content {
    margin-top: 30px;
    display: flex;
    justify-items: center;
    align-items: center;
    color: #9F9F9F;
}

.filter {
    position: relative;
}

.input-light {
        width: 100%;
        height: 45px;
        border-radius: 15px;
        background-color: #DBEBE3;
        text-decoration: none;
        border: 0px;
        padding-left: 25px;
        text-indent: 40px;
        color:#27262D ;
        transition: 0.3s all ease-in-out;

}
.input-dark {
        width: 100%;
        height: 45px;
        border-radius: 15px;
        background-color: #E6FCF3;
        text-decoration: none;
        border: 0px;
        padding-left: 25px;
        text-indent: 40px;
        transition: 0.3s all ease-in-out;

}

input::placeholder {
    color: #001014;
}
input:focus {
 outline: none;
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