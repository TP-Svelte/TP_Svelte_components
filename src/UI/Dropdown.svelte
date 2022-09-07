<script>
  export let darkMode;
  import Arrow from '/src/assets/arrow.svg';

  //// Éléments modifiables 
  // Titre Dropdown
  export let dropdownTitle = 'Dropdown button';
  // Items Dropdown
  export let dropdownItems = [
    { item: 'Option A' },
    { item: 'Option B' },
    { item: 'Option C' }
  ];
  //Couleur ellipse Dropdown
  export let EllipseColor = '#C6E0D7';
  // Image ellipse Dropdown
  export let EllipseImg = '/src/assets/list.svg';
  //Fermeture automatique du Dropdown
  export let automaticClose = false; 
  //Item Selectionné devient titre du Dropdown
  export let selectedItemIsTitle = true; 

  let openDropdown = false; 

  const toggle = () => {
    openDropdown = !openDropdown
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
    if (automaticClose) {
      toggle()
    }
  };
</script>
<div id="Dropdown">
  <button on:click={ toggle } aria-expanded={ openDropdown } class={darkMode ? 'dropdown-light' : 'dropdown-dark'}>
      <div id="ellipse_btn" style:background-color={EllipseColor}>
        <img src="{ EllipseImg }" alt="list icon">
      </div>
      <span>{ dropdownTitle }</span>
      <img id="arrow" src={ Arrow } alt="">
  </button>

  {#if openDropdown === true}
  <div id="dropdown_items" class={darkMode ? 'dropdown-light' : 'dropdown-dark'}>
      <ul>
          {#each dropdownItems as dropdownItem}

          <li class="active hidden" on:click={ selected }>
              <div id="ellipse_list" style:background-color={EllipseColor}></div>
              <p>{ dropdownItem.item } </p>
          </li>
          {/each}
      </ul>
  </div>
  {/if}
</div>

<style>
  .dropdown-dark {
    background-color: #001014;
  }
  .dropdown-light {
    background-color: #F2F2F2;
  }
  button {
    border-radius: 50px;
    display: flex;
    padding: 10px 22px 10px 14px;
    border: none;
    margin-bottom: 5px;
    cursor: pointer;
    /* margin: 50px */
  }
  button img {
    margin-top: auto;
    margin-bottom: auto;
  }
  button span {
    margin-top: auto;
    margin-bottom: auto;
    color: #9F9F9F;
    margin-right: 35px;
    font-weight: 700;
  }
  #ellipse_btn {
    width: 40px;
    height: 40px;
    border-radius:50px;
    margin-right: 15px;
    display: flex;
    justify-content: center;
  }
  #ellipse_btn > img {
    max-width: 24px;
  }

  #ellipse_list {
    width: 5px;
    height: 5px;
    margin-right: 15px;
    border-radius:50px;
    margin-bottom: auto;
    margin-top: auto;
  }
  #arrow {
    height: 20px;
    transition: transform 0.2s ease-in;
  }

  [aria-expanded=true] #arrow {
    transform: rotate(0.25turn);
  }

  #dropdown_items {
    border-radius: 20px;
    display: table;
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
    padding: 0 8px;
  }
  li p {
    color: #a3a3a3;
    margin-top: auto;
    margin-bottom: auto;
    cursor: pointer;
  }
  li p:hover {
    font-weight: 700;
  }
  .active {
    font-weight: 700;
  }
  .active.hidden{
    font-weight: 400;
  }

</style>