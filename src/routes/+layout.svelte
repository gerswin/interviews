<script>
	import '../app.css';
	import { DarkMode } from 'flowbite-svelte';
	import { Footer, FooterBrand, FooterCopyright, FooterIcon, FooterLink, FooterLinkGroup } from "flowbite-svelte"
	import { Navbar, NavBrand, NavHamburger, NavUl, NavLi, Chevron, MegaMenu } from 'flowbite-svelte'
	import logo from '$lib/images/logo-footer.svg';
</script>

<Navbar let:hidden let:toggle>
	<NavBrand href="/">
	  <img src="{logo}" class="mr-3 h-6 sm:h-9" alt="Linktic"/>
	  <span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">Entrevistas</span>
	</NavBrand>
	<NavHamburger on:click={toggle} />
	<NavUl {hidden}>
	  <NavLi href="/">Inicio</NavLi>
	</NavUl>
  </Navbar>
<slot />
<Footer>
	<FooterCopyright href="/" by="Linktic" year={2023} />
	<FooterLinkGroup ulClass="flex flex-wrap items-center mt-3 text-sm text-gray-500 dark:text-gray-400 sm:mt-0">
	</FooterLinkGroup>
</Footer>
