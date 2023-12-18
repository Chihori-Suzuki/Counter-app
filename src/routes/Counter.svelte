<script lang="ts">
  export let count: number = 0;

  export let title: string = "new";
  const increment = (): void => {
    count += 1;
  };
  const decrement = (): void => {
    count > 0 ? (count -= 1) : (count = 0);
  };
  const clear = (): void => {
    count = 0;
  };
  const changeTitle = (newTitle: string): void => {
    title = newTitle;
  };
</script>

<div
  class="w-96 rounded border-solide bg-gray-100 shadow-lg m-auto flex flex-row justify-between mb-2 p-2"
>
  <input
    bind:value={title}
    on:change={() => changeTitle(title)}
    class="text-gray-600 ml-4 px-1 w-32"
  />
  <p class="text-lg font-bold px-4">{count}</p>
  <div class="flex">
    <button
      on:click={increment}
      class="btn bg-red-400 rounded-l px-2 text-white">+</button
    >
    <button on:click={decrement} class="btn bg-blue-400 px-2 text-white"
      >-</button
    >
    <button on:click={clear} class="btn bg-yellow-400 rounded-r px-2 text-white"
      >0</button
    >
    <button on:click class="text-gray-500 cursor-pointer px-4">x</button>
  </div>
</div>
