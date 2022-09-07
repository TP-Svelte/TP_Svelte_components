<script>

import Arrow from '/src/assets/arrow.svg';
import Ellipse1 from '/src/assets/ellipse1.svg';

//// Éléments modifiables 
// Titre Dropdown
export let dropdownTitle = 'Dropdown button';
// Items Dropdown
export let dropdownItems = [
  { item: 'Option A' },
  { item: 'Option B' },
  { item: 'Option C' }
];
//Fermeture automatique du Dropdown
let automaticClose = false; 
//Item Selectionné devient titre du Dropdown
let selectedItemIsTitle = false; 
//Affiche l'item séléctionné
let showSelectedItem = false; 

let openDropdown = false; 
let ariaExpanded = false; 

const toggle = () => {
  openDropdown = !openDropdown
  ariaExpanded = !ariaExpanded
};

let elementSelected='';

function selected() {
  var liElems = document.querySelectorAll('ul > li');
  liElems.forEach(function(elem) {
    elem.classList.remove('active');
    elem.classList.remove('hidden');
  });
  this.classList.add('active');
  const activeItems = document.querySelector('.active p').innerHTML;
  if (selectedItemIsTitle) {
    dropdownTitle = activeItems;
  }
  if (showSelectedItem) {
    elementSelected = 'Vous avez choisi ' + activeItems;
  }
  if (automaticClose) {
    toggle()
  }
};

</script>

<button on:click={ toggle } aria-expanded={ ariaExpanded }>
    <img id="ellipse_btn" src={ Ellipse1 } alt="">
    <span>{ dropdownTitle }</span>
    <img id="arrow" src={ Arrow } alt="">
</button>

{#if openDropdown === true}
<div id="dropdown_items">
    <ul>
        {#each dropdownItems as dropdownItem }

        <li class="active hidden" on:click={ selected }>
            <img class="ellipses" src={ Ellipse1 } alt="">
            <p>{ dropdownItem.item } </p>
        </li>
        {/each}
    </ul>
</div>
{/if}

<p>{ elementSelected }</p>

<style>
  button {
    background-color: #F2F2F2;
    border-radius: 50px;
    display: flex;
    padding: 6px 14px 6px 8px;
    border: none;
    margin-bottom: 5px;
    /* margin: 50px */
  }
  button img {
    margin-top: auto;
    margin-bottom: auto;
  }
  button span {
    margin-top: auto;
    margin-bottom: auto;
    color: #a3a3a3;
    margin-right: 35px;
  }
  #ellipse_btn {
    margin-right: 15px;
    width: 35px;
  }
  #arrow {
    height: 20px;
    transition: transform 0.2s ease-in;
  }

  [aria-expanded=true] #arrow { transform: rotate(0.25turn); }
  .ellipses {
    width: 27px;
    margin-right: 15px;
  }
  #dropdown_items {
    background-color: #F2F2F2;
    border-radius: 20px;
    display: inline-block;
    min-width: 200px;
    padding: 5px 15px;
  }
  ul {
    padding: 0;
    margin: 0;
  }
  li {
    list-style: none;
    display: flex;
    margin-top: 15px;
    margin-bottom: 15px;
  }
  li p {
    color: #a3a3a3;
    margin-top: auto;
    margin-bottom: auto;
  }
  .active {
    font-weight: 600;
  }
  .active.hidden{
    font-weight: 400;
  }
</style>