<script lang="ts">
  import axios from 'axios';

  let email;
  let reportOptions = [
    {text: 'Arkansas'},
    {text: 'Minnesota'},
    {text: 'All'}
  ]
  let time;
  let amPm;
  let timezone;
  let message = "";
  let error = "";
  let reportOptionValue = "";

  const submitForm = async () => {
    try {

      const submit = await axios.post('/batch', {
        email: email,
        report: reportOptionValue,
        time: time,
        amPm: amPm,
        timezone: timezone,
      })
      
      const data = await submit.data;
      console.log(data);
      message = data;
    } catch (err) {
      error = err;
    }
  };
</script>

<schedule>
  <form on:submit|preventDefault={submitForm}>
    <div class="scheduleForm">
      <label for="email">Email</label>
      <input type="text" name="email" bind:value={email} />
      <label for="report">Report Option</label>
      <select type="text" name="report" bind:value={reportOptionValue}>
        <option value="" disabled>-- Select Report Type --</option>
        {#each reportOptions as reportOption}
        <option value={reportOption.text}>{reportOption.text}</option>
        {/each}
      </select>
      <label for="time">Time (PST)</label>
      <input type ="time" bind:value={time}/>
      <input type="submit" class="submit-button" />
    </div>
  </form>
</schedule>

<style>
  form {
    margin-left: 5rem;
    margin-right: 5rem;
    margin-top: 1rem;
    margin-bottom: 1rem;
    display: flex;
    justify-content: center;
  }
  .scheduleForm {
    display: flex;
    flex-direction: column;
  }

  label {
    margin-top: 1rem;
  }

  .submit-button {
    margin-top: 2rem;
    padding-top: 0.25rem;
    padding-bottom: 0.25rem;
  }

  .submit-button:hover {
    cursor: pointer;
    background-color: #543BE1;
    color: #fefefe;
  }
</style>