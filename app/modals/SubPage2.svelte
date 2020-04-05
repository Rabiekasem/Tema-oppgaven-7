<script>
  import { closeModal } from 'svelte-native'
</script>

<page class="page">
  <stackLayout>
    <stackLayout> 
      <button class="button" text="back" on:tap={() => closeModal()}/>
    </stackLayout>
  
    <stackLayout>
      <scrollView height="100%">  
        <webView src="https://www.espn.com/nba/standings" />
      </scrollView>
    </stackLayout>
  </stackLayout> 
</page>



<style>
 .button{
  width: 100%;
  background-color: white;
  margin: 0;
 }
</style>