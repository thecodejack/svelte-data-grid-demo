<script>
  import DataGrid from "svelte-data-grid-tmp";
  import TextboxCell from "svelte-data-grid-tmp/src/textbox-cell.svelte";
  import SelectCell from "svelte-data-grid-tmp/src/select-cell.svelte";
  import CheckboxCell from "svelte-data-grid-tmp/src/checkbox-cell.svelte";
  import dRows from "./dataset.json";

  let allowResizeFromTableCells = false;
  let allowResizeFromTableHeaders = true;
  let allowColumnReordering = true;
  let rowHeight = 24;
  let __affixedColumnIndices = [0];
  let rows = dRows;
  let columns = [
    {
      display: "Row #",
      dataName: "index",
      width: 60
    },
    {
      display: "Name",
      dataName: "name",
      width: 250,
      cellComponent: TextboxCell
    },
    {
      display: "Gender",
      dataName: "gender",
      width: 100,
      cellComponent: SelectCell,
      options: [
        {
          display: "Male",
          value: "male"
        },
        {
          display: "Female",
          value: "female"
        }
      ]
    },
    {
      display: "Active",
      dataName: "isActive",
      width: 75,
      cellComponent: CheckboxCell
    },
    {
      display: "Balance",
      dataName: "balance",
      width: 115
    },
    {
      display: "Age",
      dataName: "age",
      width: 45,
      cellComponent: TextboxCell
    },
    {
      display: "Eye Color",
      dataName: "eyeColor",
      width: 75,
      cellComponent: SelectCell,
      options: [
        {
          display: "Green",
          value: "green"
        },
        {
          display: "Blue",
          value: "blue"
        },
        {
          display: "Brown",
          value: "brown"
        }
      ]
    },
    {
      display: "Email",
      dataName: "email",
      width: 250,
      cellComponent: TextboxCell
    },
    {
      display: "Company",
      dataName: "company",
      width: 150,
      cellComponent: TextboxCell
    },
    {
      display: "Address",
      dataName: "address",
      width: 250,
      cellComponent: TextboxCell
    },
    {
      display: "Favorite Fruit",
      dataName: "favoriteFruit",
      width: 120
    },
    {
      display: "Registered",
      dataName: "registered",
      width: 250
    }
  ];
</script>

<style>
  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  :global(*) {
    box-sizing: border-box;
  }

  .header {
    text-align: center;
  }

  .controls {
    width: 40%;
    margin: 2em auto;
  }
  .grid-wrap {
    width: 70%;
    margin: 0 auto;
    height: calc(100vh - 300px);
    border: 1px solid black;
  }
</style>

<div class="header">
  <h1>Data Grid Demo</h1>
  <h4>40,000 rows</h4>
</div>
<div class="grid-wrap">
  <DataGrid
    {rows}
    {columns}
    bind:allowResizeFromTableCells
    bind:allowResizeFromTableHeaders
    bind:allowColumnReordering
    bind:rowHeight />
</div>
<div class="controls">
  <div>
    <label>
      <input type="checkbox" bind:checked={allowResizeFromTableCells} />
      Allow resize from table cells
    </label>
  </div>
  <div>
    <label>
      <input type="checkbox" bind:checked={allowResizeFromTableHeaders} />
      Allow resize from table headers
    </label>
  </div>
  <div>
    <label>
      <input type="checkbox" bind:checked={allowColumnReordering} />
      Allow dragging columns to new location
    </label>
  </div>
  <div>
    Row Height:
    <input type="number" bind:value={rowHeight} />
  </div>
</div>
