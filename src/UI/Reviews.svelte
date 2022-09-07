<script>
export let reviewsInfo;
export let darkMode;
import StarRating from 'svelte-star-rating';

</script>


{#each reviewsInfo as review, index}

<div class={darkMode ?  'container' : 'container-dark'}>
        <div class="content">
            <h2>{review.name}</h2>
            <div>
                <StarRating rating={review.stars} />

            </div>
            <div class="content-review">
                <h3 class={darkMode ? '' : 'title-dark'}>{review.title}</h3>
                <p>{review.description}</p>
            </div>

        </div>
</div>
{/each}


<style>
.container {
    width: 60vw;
    height: auto;
    background-color: #F2F2F2;
    padding: 2em;
    border-radius: 24px;
    text-align: left;
    margin: 2em;

}
.container-dark {

    width: 60vw;
    height: auto;
    background-color: #141316;
    padding: 2em;
    border-radius: 24px;
    text-align: left;
    margin: 2em;
}

.content {
    margin-top: 30px;
    display: flex;
    flex-direction:row;
    justify-content: space-between;
    align-content: center;
    align-items: center;
    color: #BCBCBC;
}

.content-review {
    width: 40%;
    text-align: left;
    

}
h3 {
    color: #191919;
}
.title-dark {
    color: #BCBCBC;
}
</style>