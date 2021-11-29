<script>
  import SimpleStorage from "../contracts/SimpleStorage.json"
  import { onMount } from "svelte"
  import { defaultChainStore, web3, connected } from "svelte-web3"

  let storageValue = 0
  let accounts,contract

  onMount(async () => {
    // add a test to return in SSR context
    await defaultChainStore.setBrowserProvider()
    await getContract()
    runExample()
  })

  async function getContract() {
    // Use web3 to get the user's accounts.
    accounts = await $web3.eth.getAccounts()

    // Get the contract instance.
    const networkId = await $web3.eth.net.getId()
    const deployedNetwork = SimpleStorage.networks[networkId]
    contract = new $web3.eth.Contract(
      SimpleStorage.abi,
      deployedNetwork && deployedNetwork.address
    )

  }

  async function runExample() {
    // Stores a given value, 5 by default.
    await contract.methods.set(5).send({ from: accounts[0] })

    // Get the value from the contract to prove it worked.
    const response = await contract.methods.get().call()

    storageValue = response
  }
</script>

{#if !$connected}
  <div>Loading Web3, accounts, and contract...</div>
{:else}
<div class="container">
  <div class="row">
    <div class="col-8 offset-2">
      <h1 class="text-center text-dark">Truffle Box</h1>
      <h4 class="text-center text-primary">Skeleton SvelteJS truffle box</h4>

      <!-- <Information connected={connected}></Information> -->

      <div class="alert alert-secondary">
        <h4>Smart Contract Example</h4>
        <p>
          If your contracts compiled and migrated successfully, below will show
          a stored value of 5 (by default).
        </p>
        <p>
          Try changing the value stored on <strong>line 71</strong> of
          <em>src/components/App.html</em>.
        </p>
        <p>The stored value is: {storageValue}</p>
      </div>
    </div>
  </div>
</div>
{/if}
