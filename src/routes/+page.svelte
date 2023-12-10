<script lang="ts">
  import Counter from "./Counter.svelte";

  type Counter = { id: number; title: string; count: number };
  let counters: Counter[] = [{ id: 1, title: "new", count: 0 }];
  $: maxId = 1;
  $: titleList = counters.map((counter) => counter.title);
  $: sum = counters.reduce((acc, cur): number => acc + cur.count, 0);

  const createCounter = (): void => {
    let newId: number = maxId + 1;
    counters = [...counters, { id: newId, title: "new", count: 0 }];
    maxId += 1;
  };
  const deleteCounter = (id: number): void => {
    counters = counters.filter((counter) => counter.id !== id);
  };
</script>

<svelte:head>
  <title>Multiple Counter</title>
</svelte:head>

<div class="flex flex-col items-center">
  <h1 class="text-6xl m-6">Multiple Counter</h1>

  {#each counters as counter (counter.id)}
    <Counter
      on:click={() => deleteCounter(counter.id)}
      bind:count={counter.count}
      bind:title={counter.title}
    />
  {/each}

  <button
    on:click={createCounter}
    class="w-96 m-auto text-center bg-green-400 rounded text-white cursor-pointer"
    >new counter</button
  >
  <p>title list: {titleList}</p>
  <p>sum of count: {sum}</p>
</div>
