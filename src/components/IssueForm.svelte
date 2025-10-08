<script>
  import axios from "axios";
  let studentName = "", nim = "", degree = "", result = "";

  async function issue() {
    const payload = { studentName, nim, degree, issuedAt: new Date().toISOString() };
    try {
      const res = await axios.post("/api/issue", payload);
      result = JSON.stringify(res.data, null, 2);
    } catch (e) {
      result = e.message;
    }
  }
</script>

<div>
  <h2 class="text-2xl font-semibold mb-4 text-gray-800">Issue Diploma</h2>

<div class="bg-white shadow-md rounded-2xl p-6 max-w-md space-y-4 border border-gray-100">
  <div>
    <label class="block text-sm font-medium text-gray-700 mb-1">Student Name</label>
    <input
      type="text"
      placeholder="Enter student name"
      bind:value={studentName}
      class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:outline-none"
    />
  </div>

  <div>
    <label class="block text-sm font-medium text-gray-700 mb-1">NIM</label>
    <input
      type="text"
      placeholder="Enter NIM"
      bind:value={nim}
      class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:outline-none"
    />
  </div>

  <div>
    <label class="block text-sm font-medium text-gray-700 mb-1">Degree</label>
    <input
      type="text"
      placeholder="Enter degree (e.g., B.Sc, M.Sc)"
      bind:value={degree}
      class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:outline-none"
    />
  </div>

  <button
    on:click={issue}
    class="w-full bg-blue-600 text-white py-2 rounded-lg hover:bg-blue-700 transition-colors"
  >
    Submit
  </button>
</div>

{#if result}
  <pre class="mt-6 bg-gray-100 text-sm p-4 rounded-lg text-gray-800 overflow-x-auto">{result}</pre>
{/if}

</div>
