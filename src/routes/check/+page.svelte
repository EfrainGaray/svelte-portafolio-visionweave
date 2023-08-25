<script>
// @ts-nocheck

    import { JsonView } from '@zerodevx/svelte-json-view'
		let url = '';

	let json = '';
	
    let payload = '';
	async function doPost () {
		const res = await fetch(url, {
			method: 'POST',
			body: payload,
            headers:{
                "Content-Type": "application/json"
            }
		})
		
	
		json = await res.json()
	}
</script>
<style>
    .center{
        display: flex;
        justify-content: center;
        align-items: center;
        padding-top: 5%;
    }
    .form{
        display: flex;
        justify-content: center;
        align-items: center;
        padding-top: 5%;
        flex-flow: column;
        gap: 20px;
    }
    input{
        width: 500px;
    }
    textarea{
        width: 500px;
        height: 300px;
    }
    
    button {
        cursor:pointer;
    }
    .wrap {
        background-color: #313131;
    font-family: monospace;
    font-size: 14px;
 

  }
</style>
<div class="form">
    
<input bind:value={url} placeholder="Ingresa Url" />

<textarea bind:value={payload}   placeholder="Ingresa Payload" />
</div>

<div class="center">
    <button type="button" on:click={doPost} >
        LLAMAR SERVICIO
    </button>

</div>
{#if json}
<div class="wrap" >
    <JsonView {json} />
  </div>
{/if}
