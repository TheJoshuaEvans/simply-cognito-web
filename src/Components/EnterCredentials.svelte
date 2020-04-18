<script>
  import { createEventDispatcher } from 'svelte';

  import STATES from '../../lib/utils/states.js';
  
  export let sharedData;

  const dispatch = createEventDispatcher();

  sharedData.setTest = 'set successful!';

  function changeState() {
    dispatch('changeState', {
      newState: STATES.CHOOSE_POOL
    });
  }

  function handleCredentialFormSubmit(event) {
    event.preventDefault();
    console.log(this.elements.id.value);
    console.log(this.elements.secret.value);
    console.log(event);
  }
</script>

<div class='enter-credentials-container'>
  <h2>Enter AWS Credentials</h2>
  <form on:submit={handleCredentialFormSubmit}>
    <div class='credential-input'>
      <label>
        Access Key ID: <input type='text' name='id'> 
      </label>
    </div>
    <div class = 'credential-input'>
      <label>
        Access Key Secret: <input type='password' name='secret'>      
      </label>
    </div>
    <div class = 'credential-input'>
      <button type='submit'>Submit</button>
    </div>
  </form>
</div>