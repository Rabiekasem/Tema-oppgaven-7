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
            <webView src="https://bleacherreport.com/articles/845438-the-ultimate-goat-debate#slide0" />
        </scrollView>
    </stackLayout>
</stackLayout>
</page>


<style>

 .page{
   background-color: rgb(180, 180, 179);
 }
</style>