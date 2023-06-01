<script>
	import {
		Navbar,
		NavHamburger,
		NavUl,
		NavLi,
		Chevron,
		MegaMenu,
		UserCircle,
		DarkMode,

		Input

	} from 'flowbite-svelte';
	let menu = [
		{ name: 'Pessoas', href: '/cadastros/pessoas', icon: UserCircle },
		{ name: 'Bancos', href: '/cadastros/bancos', icon: UserCircle },
		{ name: 'Mercados', href: '/cadastros/mercados', icon: UserCircle },
		{ name: 'Pets', href: '/cadastros/pets', icon: UserCircle },
		{ name: 'Items', href: '/cadastros/items', icon: UserCircle }
	];
</script>

<Navbar let:hidden let:toggle>
	<NavHamburger on:click={toggle} />
	<NavUl {hidden}>
		<NavLi href="/">Dashboard</NavLi>
		<NavLi href="/services">Tarefas</NavLi>
		<NavLi href="/services">Projetos</NavLi>
		<NavLi href="/services">Financeiro</NavLi>
		<NavLi href="/services">Estoque</NavLi>
		<NavLi href="/services">Fiscal</NavLi>
		<NavLi><Chevron aligned>Cadastros</Chevron></NavLi>
		<MegaMenu items={menu} let:item>
			<a href={item.href} class="flex items-center hover:text-blue-600 dark:hover:text-blue-500">
				<span class="sr-only">{item.name}</span>
				<svelte:component this={item.icon} class="w-4 h-4 mr-2" />{item.name}
			</a>
		</MegaMenu>
	</NavUl>
	<div class="hidden relative md:block">
		<div class="flex absolute inset-y-0 left-0 items-center pl-3 pointer-events-none">
			<svg
				xmlns="http://www.w3.org/2000/svg"
				fill="none"
				viewBox="0 0 24 24"
				stroke-width="1.5"
				stroke="currentColor"
				class="w-6 h-6 dark:text-white"
				><path
					stroke-linecap="round"
					stroke-linejoin="round"
					d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z"
				/></svg
			>
		</div>
		<Input size="sm" id="search-navbar" class="pl-10" placeholder="Search..." />
	</div>
	<DarkMode initialTheme='light' />
</Navbar>
