<script>
  import IssueForm from "./components/IssueForm.svelte";
  import VerifyForm from "./components/VerifyForm.svelte";
  let tab = 'issue';
</script>

<main class="p-4 font-sans max-w-xl mx-auto">
  <h1 class="text-2xl mb-4">🎓 Blockchain Diploma Admin</h1>
  <nav class="mb-4">
    <button on:click={() => tab='issue'}>Issue</button>
    <button on:click={() => tab='verify'}>Verify</button>
  </nav>

  {#if tab === 'issue'}
    <IssueForm />
  {:else}
    <VerifyForm />
  {/if}
</main>

<style>
  button { margin-right: 10px; padding: 5px 10px; }
</style>
