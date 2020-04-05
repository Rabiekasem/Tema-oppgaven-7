<script>
  import { closeModal } from 'svelte-native'
</script>

<page class="page">
  <stackLayout>
    <stackLayout> 
      <button class="button" text="back" on:tap={() => closeModal()}/>
    </stackLayout>
    
    <stackLayout>
        <scrollView>  
          <webView src="https://eu.usatoday.com/story/sports/nba/columnist/jeff-zillgitt/2019/03/07/nba-greatest-of-all-time-goat-lebron-james-wilt-chamberlain-michael-jordan-bill-russell-kareem/3095981002/" />
        </scrollView>
    </stackLayout>
  </stackLayout>
</page>


<style>

 .page{
   background-color: rgb(180, 180, 179);
 }
 
 .button{
   width: 100%;
   background-color: white;
   margin: 0;
 }
</style>