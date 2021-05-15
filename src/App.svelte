<script>
	import RegionData from "./RegionData.svelte";
	import {
		Grid,
		Row,
		Column,
		Tile,
		InlineLoading,
	} from "carbon-components-svelte";

	const url =
		"https://api.apify.com/v2/key-value-stores/toDWvRj1JpTXiM8FF/records/LATEST";

	let DATA;
	fetch(url)
		.then((r) => r.json())
		.then((data) => {
			DATA = data;
		});

	$: DATE = new Date(DATA?.lastUpdatedAtApify).toLocaleDateString("en-IN", {
		year: "numeric",
		month: "short",
		day: "numeric",
	});
</script>

<div class="content">
	<br />
	<h1>COVID 19 INDIA</h1>
	<br />
	<br />

	{#if DATA}
		<Grid>
			<Row>
				<Column>
					<Tile style="background: var(--cds-danger-01);">
						<h3>Confirmed</h3>
						<p>
							+{DATA.activeCasesNew +
								DATA.recoveredNew +
								DATA.deathsNew}
						</p>
						<p>{DATA.totalCases}</p>
					</Tile>
				</Column>
				<Column>
					<Tile style="background: var(--cds-interactive-01);">
						<h3>Active</h3>
						<p>+{DATA.activeCasesNew}</p>
						<p>{DATA.activeCases}</p>
					</Tile>
				</Column>
				<Column>
					<Tile style="background: var(--cds-support-02);">
						<h3>Recovered</h3>
						<p>+{DATA.recoveredNew}</p>
						<p>{DATA.recovered}</p>
					</Tile>
				</Column>
				<Column>
					<Tile>
						<h3>Deaths</h3>
						<p>+{DATA.deathsNew}</p>
						<p>{DATA.deaths}</p>
					</Tile>
				</Column>
			</Row>
		</Grid>

		<br />
		<p>Updated at {DATE}</p>
		<br />

		<RegionData regionData={DATA.regionData} />
	{:else}
		<div style="display: flex; justify-content: center;">
			<InlineLoading />
		</div>
	{/if}

	<br /><br />
	<p><b>Made by Sweety</b></p>
	<br />
</div>

<style>
	h1,
	h3,
	p {
		text-align: center;
	}
</style>
