<script>
	export let darkMode;

	//// Éléments modifiables 
	// Logo Navbar
	const logo = "https://www.pngmart.com/files/10/Apple-Logo-PNG-Clipart.png"
	// Items + Link Navbar
	export let navbarItems = [
	{ item: 'Home', link: '#' },
	{ item: 'About', link: '#' },
	{ item: 'Contact', link: '#' }
	];
</script>

<div id="Navbar">
	<div class="nav-wrapper {darkMode ? 'navbar-light' : 'navbar-dark'}">
		<div class="logo-container">
			<img class="logo" src={ logo } alt="Logo">
		</div>
		<nav>
			<input class="hidden" type="checkbox" id="menuToggle">
			<label class="menu-btn" for="menuToggle">
				<div class="menu {darkMode ? 'bm-light' : 'bm-dark'}"></div>
				<div class="menu {darkMode ? 'bm-light' : 'bm-dark'}"></div>
				<div class="menu {darkMode ? 'bm-light' : 'bm-dark'}"></div>
			</label>
			<div class="nav-container {darkMode ? 'navbar-light' : 'navbar-dark'}">
				<ul class="nav-tabs">
					{#each navbarItems as navbarItem }
						<li class="nav-tab "><a href={ navbarItem.link } class="{darkMode ? 'navlink-light' : 'navlink-dark'}">{ navbarItem.item }</a></li>
					{/each}
				</ul>
			</div>
		</nav>
	</div>
</div>

<style>
  .navbar-dark {
      background-color: #001014;
  }
  .navbar-light {
      background-color: #F2F2F2;
  }
  .navlink-dark {
      color: #E6FCF3;
  }
  .navlink-light {
      color: #9F9F9F;
  }
  .bm-dark {
    background: #E6FCF3;
  }
  .bm-light {
    background: #191919;;
  }
  .nav-wrapper {
    position: sticky;
    top: 0;
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    align-items: center;
    justify-content: space-between;
    margin: auto;
    width: 99%;
    height: 80px;
    border-radius: 0 0 24px 24px;
    padding: 0px 5px;
    z-index: 2;
  }
  .nav-wrapper nav {
    margin-right: 110px;
  }
  .logo-container {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 50px;
  }
  .logo {
    height: 60px;
  }

  .nav-tabs {
    display: flex;
    font-size: 18px;
    list-style: none;
  }
  .nav-tabs a {
    text-decoration: none;
  }
  .nav-tab:not(:last-child) {
    padding: 10px 25px;
    border-right: 1px solid #dfdfdf;
  }
  .nav-tab:last-child {
    padding: 10px 0 0 25px;
  }
  .nav-tab,
  .menu-btn {
    cursor: pointer;
  }
  .hidden {
    display: none;
  }
  @media screen and (max-width: 800px) {
    .nav-container {
      position: fixed;
      display: none;
      overflow-y: auto;
      z-index: 3;
      top: 0;
      right: 0;
      width: 270px;
      height: 100%;
      border-bottom-left-radius: 50px;
    }
    .nav-wrapper nav {
      margin-right: 50px;
    }
    .logo-container {
      margin-left: 20px;
    }
    .nav-tabs {
      flex-direction: column;
      align-items: flex-end;
      margin-top: 80px;
      width: 100%;
    }
    .nav-tab:not(:last-child) {
      padding: 20px 41px;;
      margin: 0;
      border-right: unset;
      border-bottom: 1px solid #dfdfdf;
    }
    .nav-tab:last-child {
      padding: 20px 41px;
    }
    .menu-btn {
      position: relative;
      display: block;
      margin: 0;
      width: 20px;
      cursor: pointer;
      z-index: 3;
    }
    .menu-btn .menu {
      height: 2px;
      border-radius: 2px;
    }
    .menu-btn .menu:nth-child(2) {
      margin-top: 4px;
      opacity: 1;
    }
    .menu-btn .menu:nth-child(3) {
      margin-top: 4px;
    }
    #menuToggle:checked + .menu-btn .menu {
      transition: transform 0.2s ease;
    }
    #menuToggle:checked + .menu-btn .menu:nth-child(1) {
      transform: translate3d(0, 6px, 0) rotate(45deg);
    }
    #menuToggle:checked + .menu-btn .menu:nth-child(2) {
      transform: rotate(-45deg) translate3d(-5.71429px, -6px, 0);
      opacity: 0;
    }
    #menuToggle:checked + .menu-btn .menu:nth-child(3) {
      transform: translate3d(0, -6px, 0) rotate(-45deg);
    }
    #menuToggle:checked ~ .nav-container {
      z-index: 1;
      display: flex;
      animation: menu-slide-left 0.3s ease;
      position: absolute;
      top: 0px;
      height: auto;
    }
    @keyframes menu-slide-left {
      0% {
        transform: translateX(100px);
      }
      to {
        transform: translateX(0);
      }
    }
  }
</style>
