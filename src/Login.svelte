<script>
  import { Row, Col, TextField, Button } from 'svelte-materialify/src';
  import { replace } from 'svelte-spa-router';
  import {userStore} from '../stores/user';

  let username;
  let password;

  async function onSubmit() {
    

    let {type} = "admin";

    userStore.subscribe(userStore => ({
      username,
      password,
      type
    }));
    console.log(userStore);
    if(type === 'USER') {
      replace('/');
    } else {
      replace('/controlPanel');
    }
  }
</script>

<div class="mb-10 d-flex flex-column align-center justify-center mt-4">
  <TextField bind:value={username} outlined style="width:350px;">Username</TextField>
  <TextField type="password" bind:value={password} outlined style="width:350px;">Password</TextField>
  <Button name="submit" on:click={onSubmit} class="ma-5">Submit</Button>
</div>