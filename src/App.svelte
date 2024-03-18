<script>
	import Sidebar from "./components/Sidebar.svelte";

	let isOpen = true;

	function toggleMenu() {
		isOpen = !isOpen;
	}

	function handleSidebarChange(event) {
		isOpen = event.detail.isOpen;
	}
</script>

<Sidebar {isOpen} on:sidebarChange={handleSidebarChange} />
<div class="main-wrap">
	<div class="resp-menu-bar">
		<!-- svelte-ignore a11y-invalid-attribute -->
		<a href="#">
			<svg
				width="32"
				height="32"
				viewBox="0 0 32 32"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					fill-rule="evenodd"
					clip-rule="evenodd"
					d="M32 16C32 7.16344 24.8366 0 16 0C7.16344 0 0 7.16344 0 16C0 24.8366 7.16344 32 16 32H32V16Z"
					fill="#C7D100"
				/>
				<path
					d="M13.0147 17.425L16.3167 21H14.3147L11.6627 17.919V21H10.1807V11.38H11.6627V16.97L14.2627 13.837H16.3167L13.0147 17.425ZM17.86 22.3L22.15 10.054H23.281L18.991 22.3H17.86Z"
					fill="#101419"
				/>
			</svg>
		</a>
		<button class="icon-btn" on:click={toggleMenu}>
			<svg
				width="40"
				height="40"
				viewBox="0 0 40 40"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<circle
					cx="20"
					cy="20"
					r="19"
					fill="var(--bg-color-2)"
					stroke="#9DA0A7"
					stroke-width="2"
				/>
				<line
					x1="12"
					y1="15"
					x2="27"
					y2="15"
					stroke="var(--text-color)"
					stroke-width="2"
				/>
				<line
					x1="12"
					y1="20"
					x2="27"
					y2="20"
					stroke="var(--text-color)"
					stroke-width="2"
				/>
				<line
					x1="12"
					y1="25"
					x2="27"
					y2="25"
					stroke="var(--text-color)"
					stroke-width="2"
				/>
			</svg>
		</button>
	</div>
	<main>
		<h1 class="t-1">My progress</h1>
	</main>
</div>

<style>
	.resp-menu-bar {
		display: none;
		align-items: center;
		justify-content: space-between;
		background-color: var(--resp-menu-color);
		padding: 0.5rem;
		box-shadow: 0 0 0 0 #0000, 0 0 0 0 #0000, 0 0 0 0 #0000;

	}

	@media (max-width: 1025px) {
		.resp-menu-bar {
			display: flex;
		}
	}
</style>
