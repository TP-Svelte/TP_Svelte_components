<script>
export let darkMode;

</script>

<div class={darkMode ? "container" : "container-dark"}>
    <h1>
    Docs
    Components
    Blog
    JobsNew
    Theme
    Tailwind CSS on GitHub
    Rapidly build modern websites without ever leaving your HTML.</h1>
    <p>A utility-first CSS framework packed with classes like flex, pt-4, text-center and <br> rotate-90 that can be composed to build any design, directly in your markup.</p>
</div>
<style>
.container {
    margin-bottom: 75px;
    color: #001014;
    transition: 0.3s all ease-in-out;
    width: 100%;

}
.container-dark {
    margin-bottom: 75px;
    color: #E6FCF3;
    transition: 0.3s all ease-in-out;
    width: 100%;


}
h1 {
}
</style>