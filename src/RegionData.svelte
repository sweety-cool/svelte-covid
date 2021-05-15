<script>
    import { DataTable } from "carbon-components-svelte";
    export let regionData = [];

    const rows = regionData.map((r, i) => ({ ...r, id: "id" + i }));

    const headers = [
        { key: "region", value: "State / UT" },
        { key: "newInfected", value: "New Cases" },
        { key: "recovered", value: "Recovered" },
        { key: "newRecovered", value: "New Recoverd" },
        { key: "deceased", value: "Deceased" },
        { key: "newDeceased", value: "New Deaths" },
        { key: "totalInfected", value: "Total" },
    ];
</script>

<div class="regionData">
    <DataTable sortable="true" size="short" {headers} {rows} />
</div>

<style>
</style>
