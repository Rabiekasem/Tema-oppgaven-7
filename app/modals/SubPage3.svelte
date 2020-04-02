<script>
  import { closeModal } from 'svelte-native'
</script>

<page class="page">
<stackLayout>
    <stackLayout> 
       <button text="back" on:tap={() => closeModal()}/>
    </stackLayout>
    
    <stackLayout>
        <scrollView>  
            <webView src="https://www.jumpropedudes.com/workouts/lebron-james-body-breakdown" />
        </scrollView>
    </stackLayout>
</stackLayout>
</page>


<style>

 .page{
   background-color: rgb(180, 180, 179);
 }
</style>