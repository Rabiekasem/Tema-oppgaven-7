<script>
  
  import { closeModal } from 'svelte-native'
  export let article
</script>

  <page class="page">
<scrollView>
      <stackLayout class="stack">
        <label textWrap={true} class = "h1" text= "{article.title}" />
        <label class = "h1" text= "{article.author}" />
        <label textWrap={true} class = "h1" text= "{article.description}" />
        <image 
          src = "{article.urlToImage}"
          stretch = "aspectFit"
        />
        <button on:tap = { () =>closeModal()} text="close"/>            
        
      </stackLayout>
</scrollView>
  </page>



<style>
 .stack{
     padding: 24;
 }

 .page{
   background-color: rgb(180, 180, 179);
 }
</style>