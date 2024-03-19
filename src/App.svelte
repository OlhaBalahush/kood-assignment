<script>
	import Sidebar from "./components/Sidebar.svelte";
	import LineChart from "./components/LineChart.svelte";
    import VerticalBar from "./components/VerticalBar.svelte";

	let isOpen = true;
	let lineChart;
	let verticalBar;
	let mNum = 1;

	let skills = [
		{
			skill: "mobile development",
			doneProjects: 4,
			allProjects: 20,
			firstProject: "mobile-app-1",
		},
		{
			skill: "web development",
			doneProjects: 20,
			allProjects: 25,
			firstProject: "web-app-1",
		},
		{
			skill: "data analysis",
			doneProjects: 10,
			allProjects: 18,
			firstProject: "data-analysis-1",
		},
		{
			skill: "machine learning",
			doneProjects: 9,
			allProjects: 30,
			firstProject: "ml-project-1",
		},
		{
			skill: "cloud computing",
			doneProjects: 3,
			allProjects: 15,
			firstProject: "cloud-project-1",
		},
		{
			skill: "cybersecurity",
			doneProjects: 8,
			allProjects: 22,
			firstProject: "security-project-1",
		},
	];

	let upcomingSkills = [
		{
			skill: "networking",
			doneProjects: 0,
			allProjects: 10,
			firstProject: "networking-project-1",
		},
		{
			skill: "game development",
			doneProjects: 0,
			allProjects: 20,
			firstProject: "game-dev-1",
		},
		{
			skill: "devops",
			doneProjects: 0,
			allProjects: 15,
			firstProject: "devops-project-1",
		},
		{
			skill: "blockchain",
			doneProjects: 0,
			allProjects: 25,
			firstProject: "frameworks-project-1",
		},
	];

	function toggleMenu() {
		isOpen = !isOpen;
	}

	function handleSidebarChange(event) {
		isOpen = event.detail.isOpen;
	}

	function selectTimeline(months) {
		mNum = months;
		lineChart.updateChart(months);
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
			<div class="pd15 cont col-span-4 row-span-2 skills-cont">
				<h2 class="t-2">Skills</h2>
				<div class="done-skills-cont">
					{#each skills as skill}
						<div class="skill-cont">
							<div class="fr sb">
								<div class="upper-t">{skill.skill}</div>
								<div class="add-t">
									{skill.doneProjects} / {skill.allProjects}
									projects
								</div>
							</div>
							<div class="gray-line">
								<div class="p-line" style="width: calc({skill.doneProjects / skill.allProjects * 100}%);">
									<span>
										{(skill.doneProjects / skill.allProjects * 100).toFixed(0)}%
									</span>
								</div>
							</div>
						</div>
					{/each}
				</div>
				<div class="up-skills" >Upcoming Skills</div>
				<div>
					{#each upcomingSkills as skill}
						<div class="fr sb up-skill">
							<div class="fr g1">
								<div class="line">
									<div class="bullet-point"></div>
								</div>
								<div class="upper-t m">{skill.skill}</div>
							</div>
							<div class="add-t m">
								{skill.allProjects} projects |
								<!-- svelte-ignore a11y-invalid-attribute -->
								<a class="skill-a" href="#">{skill.firstProject}</a>
							</div>
						</div>
					{/each}
				</div>
			</div>
			<div class="pd15 cont col-span-8">
				<h2 class="t-2">Distribution of Users by XP</h2>
				<VerticalBar bind:this={verticalBar}/>
			</div>
			<div class="pd15 cont col-span-8">
				<h2 class="t-2">Badges</h2>
			</div>
		</div>
	</main>
</div>

<style>
	.resp-menu-bar {
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
		max-width: 1168px; /* Set the maximum width */
		width: auto; /* Allow it to shrink if content is smaller */
		box-shadow:
			0 0 0 0 #0000,
			0 0 0 0 #0000,
			0 0 0 0 #0000;
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

	.line {
		height: 100%;
		width: 2px;
		background-color: var(--gray-1);

		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
	}

	.bullet-point {
		width: 8px;
		height: 8px;
		border-radius: 50%;
		background-color: var(--gray-1);
	}

	.up-skills {
		border-bottom: 1px solid var(--gray-1);
		padding-bottom: 0.25rem;
	}

	.skill-cont {
		display: flex;
		flex-direction: column;
		gap: 0.375rem;
	}

	.done-skills-cont {
		display: flex;
		flex-direction: column;
		gap: 0.75rem;
	}

	.up-skill{
		height: 35px;
	}

	.skill-a {
		text-decoration: underline;
	}

	.gray-line {
		background-color: var(--bg-color-1);
		height: 1rem;
		border-radius: 0.5rem;
	}

	.p-line {
		height: 100%;
		background-color: var(--accent-2);
		text-align: right;
		border-radius: 0.5rem;
		font-size: var(--add-text-font-size);
	}

	.p-line span{
		padding-right: 0.5rem;
		color: var(--text-light);
	}

	@media (max-width: 1025px) {
		.resp-menu-bar {
			display: flex;
		}
	}
</style>
