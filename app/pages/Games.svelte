<script>
import {goBack} from "svelte-native"
import {navigate} from "svelte-native"
import News from "./News.svelte"
import App from "../App.svelte"

const showMain = async() =>{
        await navigate({
            page: App,
            props:{
                msg:"hi"
            }
        })
    }

    const showNews = async() =>{
        await navigate({
            page: News,
            props:{
                msg:"hi"
            }
        })
    }
</script>

<page class="page">
  <actionBar title="Games">
	<navigationButton text="Go back" android.systemIcon="ic_menu_back" on:tap="{goBack}" />
  </actionBar>

  <stackLayout>
      <flexboxLayout class="buttonsMain" alignItems="flex-start" backgroundColor="">
	    <button text="Main" width="70" height="70" backgroundColor="#4383b8" on:tap={() => showMain()}/>
	    <button text="News" width="70" height="70" backgroundColor="#4383b8"  on:tap={() => showNews()}/>
	    <button text="Games" width="70" height="70" backgroundColor="#4383b8"/>
      </flexboxLayout>
    </stackLayout>
</page>

<style>
 .page{
     background-color: rgb(138, 145, 245);
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