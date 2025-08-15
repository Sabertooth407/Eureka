<script>
  import { onMount } from "svelte";

  let prelim = [];
  let final = [];

  const prelimurl = "https://docs.google.com/spreadsheets/d/e/2PACX-1vRMkfYL8_JJSpaQVHExPgCP2DtZji1ADjc2pJrwSDw5tCGg8EGxwsLs1C3tQXPjelRy8E2cqWKfCtfE/pub?gid=0&single=true&output=csv";
  const finalurl = "https://docs.google.com/spreadsheets/d/e/2PACX-1vRMkfYL8_JJSpaQVHExPgCP2DtZji1ADjc2pJrwSDw5tCGg8EGxwsLs1C3tQXPjelRy8E2cqWKfCtfE/pub?gid=1843546568&single=true&output=csv";

  async function fetchSchedule(url) {
    const res = await fetch(url);
    const text = await res.text();
    const rows = text.split("\n").map(r => r.split(","));
    return rows.slice(1).map(row => ({
      event: row[0],
      time: row[1],
      venue: row[2]
    }));
  }

  onMount(async () => {
    prelim = await fetchSchedule(prelimurl);
    final = await fetchSchedule(finalurl);
  });
</script>

<style>
  h1 {
    text-align: center;
    color: white;
    font-family: 'Transcity DEMO', sans-serif;
    font-size: 3rem;
  }

  table {
    width: 90%;
    margin: -1rem auto;
    border-collapse: collapse;
    font-family: 'FuturaBold', sans-serif;
    background: rgba(0, 0, 0, 0.6);
    color: white;
    border-radius: 8px;
    overflow: hidden;
  }

  th, td {
    padding: 0.5rem;
    border-bottom: 1px solid rgba(255, 255, 255, 0.2);
    text-align: center;
  }

  th {
    background: #ff6ec4;
    color: white;
    text-transform: uppercase;
  }
</style>

<h1>Prelims Schedule</h1>
<table>
  <thead>
    <tr>
      <th>Event</th>
      <th>Timing</th>
      <th>Venue</th>
    </tr>
  </thead>
  <tbody>
    {#each prelim as row}
      <tr>
        <td>{row.event}</td>
        <td>{row.time}</td>
        <td>{row.venue}</td>
      </tr>
    {/each}
  </tbody>
</table>

<h1>Finals Schedule</h1>
<table>
  <thead>
    <tr>
      <th>Event</th>
      <th>Timing</th>
    </tr>
  </thead>
  <tbody>
    {#each final as row}
      <tr>
        <td>{row.event}</td>
        <td>{row.time}</td>
      </tr>
    {/each}
  </tbody>
</table>
