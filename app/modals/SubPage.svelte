<script>

  import { closeModal } from 'svelte-native'
  export let article

</script>

<page class="page">
  <scrollView>
    <stackLayout class="stack">
      <label class="label1" textWrap={true} text= "{article.title}" />
      <label class="line"/>
      <label class="label2" marginTop="10" text= "By {article.author}" />
      <label class="label3" textWrap={true} text= "{article.description}" />
      <image class="img-rounded" marginTop="10"
        src = "{article.urlToImage}"
        stretch = "aspectFit"
      />
      <button marginTop="10" on:tap = { () => closeModal()} text="close"/>              
    </stackLayout>
  </scrollView>
</page>



<style>
 .stack{
    padding: 24;
 }

 .page{
    background-color: #e2e2e2;
 }

 .label1{
   font-size: 40;
 }

 .label3{
   font-size: 20;
 }
 
 .line{
    width: 80%;
    height: 1;
    background-color: white;
    margin: 15;
  }

</style>