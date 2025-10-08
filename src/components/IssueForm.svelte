<script>
  import axios from "axios";
  let studentName = "", nim = "", degree = "", result = "";

  async function issue() {
    const payload = { studentName, nim, degree, issuedAt: new Date().toISOString() };
    try {
      const res = await axios.post("http://localhost:3001/issue", payload);
      result = JSON.stringify(res.data, null, 2);
    } catch (e) {
      result = e.message;
    }
  }
</script>

<div>
  <h2>Issue Diploma</h2>
  <input placeholder="Student Name" bind:value={studentName} />
  <input placeholder="NIM" bind:value={nim} />
  <input placeholder="Degree" bind:value={degree} />
  <button on:click={issue}>Submit</button>
  <pre>{result}</pre>
</div>
