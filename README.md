# test-of-duckdb-parquet-ranged
Quick test to see if Observable Framework can use ranged HTTP requests when querying a Parquet file.

Quick test to see if Quarto can use ranged HTTP requests when querying a Parquet file. Compare the [Quarto](https://github.com/jimjam-slam/test-quarto-duckdb-parquet-ranged) test and the [Observable notebook](https://observablehq.com/@jimjamslam/ranged-parquet-duckdb-test) test — Observable Framework uses a newer version of DuckDB-WASM, so that might be why it's the one that seems to work!

## Host tests:

**Host**         | **Works?** | **Comment**
-----------------|------------|--------------
GitHub raw URL   | ✅ Yes     | Still ends up downloading the whole file, but it's not falling back
GitHub Pages     | ✅ Yes     | Still ends up downloading the whole file, but it's not falling back

# DuckDB Ranged Parquet Read Test

This is an [Observable Framework](https://observablehq.com/framework) project. To start the local preview server, run:

```
npm run dev
```

Then visit <http://localhost:3000> to preview your project.

For more, see <https://observablehq.com/framework/getting-started>.
