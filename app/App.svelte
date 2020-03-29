
<script>
    import {navigate} from "svelte-native"
    import News from "./pages/News.svelte"
    import Games from "./pages/Games.svelte"

    const showNews = async() =>{
        await navigate({
            page: News,
            props:{
                msg:"hi"
            }
        })
    }

    const showGames = async() =>{
        await navigate({
            page: Games,
            props:{
                msg:"hi"
            }
        })
    }
</script>


<page class="page">

    <actionBar title="Main page" />
    <stackLayout>
      <flexboxLayout class="buttonsMain" alignItems="flex-start" backgroundColor="">
	    <button text="Main" width="70" height="70" backgroundColor="#4383b8"/>
	    <button text="News" width="70" height="70" backgroundColor="#4383b8" on:tap={() => showNews()}/>
	    <button text="Games" width="70" height="70" backgroundColor="#4383b8" on:tap={() => showGames()}/>
      </flexboxLayout>
    </stackLayout>
    

    
    
</page>



<style>
 .page{
     background-color: coral;
 }

 .buttonsMain{
     display: flex;
     align-items: center;
     justify-content: center;
     padding-top: 10;
 }

 .buttonsMain > button{
     border-radius: 20% 0 20% 0;
     margin: 20 20;
     color: antiquewhite
 }
</style>
