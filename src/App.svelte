<script>
    // importing components
	import Sidebar from "./components/Sidebar.svelte";
	import LineChart from "./components/LineChart.svelte";
    import SkillsComponent from "./components/SkillsComponent.svelte";
	import VerticalBar from "./components/VerticalBar.svelte";
    import BadgesComponent from "./components/BadgesComponent.svelte";

	// state variable to control the sidebar's open/close state
	let isOpen = true;
	// references to the chart components for calling methods on them
	let lineChart;
	let verticalBar;
	// variables to store selected timeline for the line chart and column count for the bar chart
	let mNum = 1;
	let bNum = 50;
	// check for small screen size, which will affect layout responsiveness
	const isSmallScreen = window.innerWidth < 900;

	// toggles the sidebar's open/close state fro small screen
	function toggleMenu() {
		isOpen = !isOpen;
	}

	// handles change event from the sidebar, updating its open/close state
	function handleSidebarChange(event) {
		isOpen = event.detail.isOpen;
	}

	// updates the line chart based on the selected timeline
	function selectTimeline(months) {
		mNum = months;
		lineChart.updateChart(months);
	}

	// updates the bar chart based on the selected range
	function updateBarRange(num) {
		bNum = num;
		verticalBar.updateChart(num);
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
		<h1 class="t-1 mb15">My progress</h1>
		<div class="grid-cont">
			<div class="pd15 cont col-span-12">
				<div class="chart-top-line">
					<h2 class="t-2">Total XP - 3.06 MB</h2>
					<div class="btn-g-bar">
						<button
							class="btn-g {mNum == 1 ? 'btn-g-act' : ''}"
							on:click={() => selectTimeline(1)}>1M</button
						>
						<button
							class="btn-g {mNum == 3 ? 'btn-g-act' : ''}"
							on:click={() => selectTimeline(3)}>3M</button
						>
						<button
							class="btn-g {mNum == 6 ? 'btn-g-act' : ''}"
							on:click={() => selectTimeline(6)}>6M</button
						>
						<button
							class="btn-g {mNum == 12 ? 'btn-g-act' : ''}"
							on:click={() => selectTimeline(12)}>1Y</button
						>
					</div>
				</div>
				<LineChart bind:this={lineChart} />
			</div>
			<div
				class="pd15 cont {isSmallScreen
					? 'col-span-12'
					: 'col-span-5 row-span-2'} skills-cont"
			>
				<h2 class="t-2">Skills</h2>
				<SkillsComponent />
			</div>
			<div
				class="pd15 cont {isSmallScreen ? 'col-span-12' : 'col-span-7'}"
			>
				<div class="chart-top-line">
					<h2 class="t-2">Distribution of Users by XP</h2>
					<div class="ranges-roll-cont">
						<div class="fr sb">
							<span>XP ranges</span>
							<span>{bNum}</span>
						</div>
						<input
							class="ranges-roll"
							type="range"
							min="2"
							max="100"
							value={bNum}
							style="--percentage: {bNum}%;"
							on:input={(e) => updateBarRange(+e.target.value)}
						/>
					</div>
				</div>
				<VerticalBar bind:this={verticalBar} />
			</div>
			<div
				class="pd15 cont {isSmallScreen ? 'col-span-12' : 'col-span-7'}"
			>
				<h2 class="t-2">Badges</h2>
				<BadgesComponent />
			</div>
		</div>
	</main>
</div>

<style>
	.resp-menu-bar {
		position: fixed;
		width: calc(100vw - 1rem);
		z-index: 900;

		display: none;
		align-items: center;
		justify-content: space-between;
		background-color: var(--resp-menu-color);
		padding: 0.5rem;
		box-shadow:
			0 0 0 0 #0000,
			0 0 0 0 #0000,
			0 0 0 0 #0000;
	}

	.cont {
		background-color: var(--bg-color-2);
		border-radius: 0.5rem;
		width: auto;
		box-shadow:
			0 0 0 0 #0000,
			0 0 0 0 #0000,
			0 0 0 0 #0000;

		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	.grid-cont {
		display: grid;
		gap: 1.5rem;
	}

	.chart-top-line {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}

	.btn-g-bar {
		display: flex;
		background-color: var(--bg-color-1);
		border-radius: 0.5rem;
	}

	.btn-g {
		min-width: 40px;
		width: 100%;
		min-height: 25px;
		background-color: transparent;
		color: var(--text-color);
		border-style: none;
		border-radius: 0.5rem;
		transition: all 0.3s ease;
	}

	.btn-g:hover {
		background-color: var(--btn-active);
	}

	.btn-g-act {
		background-color: var(--accent);
		color: white;
		pointer-events: none;
	}

	.skills-cont {
		display: flex;
		flex-direction: column;
		gap: 1.5rem;
	}

	.ranges-roll-cont {
		min-width: 200px;
	}

	.ranges-roll {
		min-width: 200px;
		width: 100%;
		margin: 0;
	}

	input[type="range"] {
		-webkit-appearance: none;
		appearance: none;
		width: 100%;
		background: var(--bg-color-1);
		cursor: pointer;
		height: 2px;
	}

	input[type="range"]::-webkit-slider-runnable-track {
		background: linear-gradient(
			to right,
			var(--accent) 0%,
			var(--accent) var(--percentage, 0%),
			var(--bg-color-1) var(--percentage, 0%),
			var(--bg-color-1) 100%
		);
		height: 2px;
	}

	input[type="range"]::-webkit-slider-thumb {
		-webkit-appearance: none;
		background-color: var(--accent);
		width: 1rem;
		height: 1rem;
		border-radius: 50%;
		margin-top: -9px; /* Adjusts the position to ensure it's centered on the track */
	}

	@media (max-width: 1025px) {
		.resp-menu-bar {
			display: flex;
		}

		.cont {
			padding: 1rem;
		}

		.chart-top-line {
			flex-direction: column;
			align-items: flex-start;
			gap: 1rem;
		}

		.ranges-roll-cont {
			width: 100%;
		}

		.btn-g-bar {
			width: 100%;
		}
	}
</style>
