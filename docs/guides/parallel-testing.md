---
slug: "/parallel-testing"
title: "Parallel Testing"
---

# Parallel Testing (Sharding)

Boost test suite efficiency with Argos Parallel Testing: Automate and streamline concurrent test executions across multiple environments effortlessly.

## Playwright

Argos seamlessly integrates with Playwright, offering out-of-the-box support for [Playwright tests sharding](https://playwright.dev/docs/test-sharding). This means zero configuration hassle for you. For more details, refer to the [Argos Playwright SDK](/playwright).

If you use an advanced orchestration system like the excellent one from [Currents](https://currents.dev), use `argos finalize`.

## Other SDKs

For environments beyond Playwright, Argos facilitates sharding through two key environment variables, simplifying the setup:

- `ARGOS_PARALLEL`: Activate the parallel mode.
- `ARGOS_PARALLEL_TOTAL`: Specifies the number of parallel nodes. It's crucial to ensure equal calls to Argos upload across these nodes.
- `ARGOS_PARALLEL_INDEX`: Specifies the index of the current parallel node.
- `ARGOS_PARALLEL_NONCE`: A unique identifier for each build. In most CI environments, Argos will automatically generate this for you.

{% hint style="info" %}
Alternatively, use `--parallel`, `--parallel-nonce`, `--parallel-total` and `--parallel-index` flags with the CLI or `parallel:  nonce: string, total: number, index: number ` within SDK options.
{% endhint %}

## Modes

There is two parallel modes available:

- If `ARGOS_PARALLEL_TOTAL` is set to a `number`, Argos will wait for this number of upload before finalizing the build.
- If `ARGOS_PARALLEL_TOTAL` is set to `-1`, Argos will wait for a `argos finalize` call to finalize the build.

### Implementing in GitHub Actions

#### With a known number of shards

Below is a practical example showcasing how to configure Argos sharding within a GitHub Actions workflow.

```yml
// .github/workflows/ci.yml
jobs:
  e2e-tests:
    timeout-minutes: 60
    runs-on: ubuntu-latest
    strategy:
      fail-fast: false
      matrix:
        shardIndex: [1, 2, 3, 4]
        shardTotal: [4]
    steps:
      # ---
      # Here you setup your repo and run your E2E tests
      # ---
      - name: Upload screenshots to Argos
        env:
          ARGOS_PARALLEL: true
          ARGOS_PARALLEL_TOTAL: ${ matrix.shardTotal }
          ARGOS_PARALLEL_INDEX: ${ matrix.shardIndex }
          # ARGOS_PARALLEL_NONCE is automatically detected

        run: npm exec -- argos upload ./screenshots
```

#### With a finalize call

Below is a practical example showcasing how to configure Argos sharding within a GitHub Actions workflow.

```yml
// .github/workflows/ci.yml
jobs:
  e2e-tests:
    timeout-minutes: 60
    runs-on: ubuntu-latest
    strategy:
      fail-fast: false
      matrix:
        shardIndex: [1, 2, 3, 4]
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
      - run: npm ci
      # ---
      # Here you setup your repo and run your E2E tests
      # ---
      - name: Upload screenshots to Argos
        env:
          ARGOS_PARALLEL: true
          ARGOS_PARALLEL_TOTAL: -1
          ARGOS_PARALLEL_INDEX: ${ matrix.shardIndex }
          # ARGOS_PARALLEL_NONCE is automatically detected

        run: npm exec -- argos upload ./screenshots

  finalize:
    timeout-minutes: 60
    runs-on: ubuntu-latest
    # Finalize the build even if some shards have failed
    if: ${ always() }
    needs: ["e2e-tests"]
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
      - run: npm ci
      - name: Finalize argos build
        env:
          # ARGOS_PARALLEL_NONCE is automatically detected

        run: npm exec -- argos finalize
```
