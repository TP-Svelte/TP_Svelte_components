<script>
// variables
    let number = 0;

// fonctions
    const supNumber = () => {
        if(number < 10){
            number ++;
        }
    }
    const subNumber = () => {
        if(number > 0){
            number --;
        }
    }
</script>


<button on:click={ supNumber }>
    +
</button>


<p>{number}</p>

<button on:click={ subNumber }>
    -
</button>


<style>

</style>