<script>
  import axios from "axios";
  let studentName = "", nim = "", degree = "", result = "";

  async function verify() {
    const payload = { studentName, nim, degree };
    try {
      const res = await axios.post("http://localhost:3001/verify", payload);
      result = JSON.stringify(res.data, null, 2);
    } catch (e) {
      result = e.message;
    }
  }
</script>

<div>
  <h2>Verify Diploma</h2>
  <input placeholder="Student Name" bind:value={studentName} />
  <input placeholder="NIM" bind:value={nim} />
  <input placeholder="Degree" bind:value={degree} />
  <button on:click={verify}>Check</button>
  <pre>{result}</pre>
</div>
