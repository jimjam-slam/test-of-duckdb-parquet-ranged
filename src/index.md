---
toc: false
---

<style>

.hero {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: var(--sans-serif);
  margin: 4rem 0 8rem;
  text-wrap: balance;
  text-align: center;
}

.hero h1 {
  margin: 2rem 0;
  max-width: none;
  font-size: 14vw;
  font-weight: 900;
  line-height: 1;
  background: linear-gradient(30deg, var(--theme-foreground-focus), currentColor);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero h2 {
  margin: 0;
  max-width: 34em;
  font-size: 20px;
  font-style: initial;
  font-weight: 500;
  line-height: 1.5;
  color: var(--theme-foreground-muted);
}

@media (min-width: 640px) {
  .hero h1 {
    font-size: 90px;
  }
}

</style>

<div class="hero">
  <h1>DuckDB Ranged Parquet Read Test</h1>
  <h2>Let's see if we can avoid reading a <em>whole</em> Parquet file.</h2>
  <a href="https://observablehq.com/framework/getting-started">Get started<span style="display: inline-block; margin-left: 0.25rem;">↗︎</span></a>
</div>

```sql
SELECT
  date, tmax
FROM
  read_parquet(${`https://raw.githubusercontent.com/jimjam-slam/test-quarto-duckdb-parquet-ranged/main/data/acorn-sat.parquet`})
WHERE
    site_num == '086338'
LIMIT 5
```

This looks like it is indeed doing a partial read! It still ends up basically reading the whole file in pieces (maybe it depends on the query you use?), but it's not falling back to a full read.
