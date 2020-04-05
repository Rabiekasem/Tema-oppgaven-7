<script>
  import {goBack} from "svelte-native"
  import {navigate} from "svelte-native"
  import {showModal} from 'svelte-native'
  import SubPage2 from "../modals/SubPage2.svelte"
  
  import News from "./News.svelte"
  import App from "../App.svelte"
  
  import FirestoreParser from "firestore-parser"
  let items = []
  const baseUrl = "https://firestore.googleapis.com/v1/"
  const productsUrl = baseUrl + "projects/my-first-firestore-proje-9c783/databases/(default)/documents/nba-data-2"  
  import { registerNativeViewElement } from 'svelte-native/dom'

  registerNativeViewElement("cardView", () => 
    require("@nstudio/nativescript-cardview").CardView
  )  

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
                msg:""
            }
        })
  }  
  const showNba = async() =>{
        await showModal({
            page: SubPage2,
            fullscreen: true,
            props:{
                msg: ""
            }
        })
  }  
  const getProducts = () => {
        fetch(productsUrl)
        .then(response => response.json())
        .then(json => FirestoreParser(json))
            .then(parsed =>{
                items = parsed.documents
                console.log(items)
             })
        .catch(error => console.lgo(error))  
  }
  getProducts()

</script>


<page class="page" actionBarHidden={true}>

    <stackLayout>
        <stackLayout>
            <flexboxLayout class="buttonsMain" alignItems="flex-start" backgroundColor="">
 	            <button text="Main" width="70" height="30" backgroundColor="" on:tap={() => showMain()}/>
 	            <button text="News" width="70" height="30" backgroundColor="" on:tap={() => showNews()}/>
 	            <button text="Games" width="70" height="30" backgroundColor=""/>
            </flexboxLayout>
        </stackLayout>
    
        
        <scrollView class="scrollOne" height="100%">
            <stackLayout class="stackOne">
              {#each items as item}
                <cardView class="card" elevation="100" margin="25" height="300" width="70%">
                    <flexboxLayout class="stackTwo" flexDirection="column" on:tap={() => showNba()} >
                        <image src="{item.fields.IMG}" stretch="aspectFit" />
                        <label class="h1" text={item.fields.teamName}/>
                        <label class="p" text= "Win: {item.fields.W}"/>
                        <label class="p" text= "Lose: {item.fields.L}"/>
                        <label class="line"/>
                        <label class="p" text= "Rebound: {item.fields.R}"/>
                        <label class="p" text= "Asisst: {item.fields.A}"/>   
                    </flexboxLayout>
                </cardView>
              {:else}
                <activityIndicator busy={true}/>
              {/each}
            </stackLayout>
        </scrollView>
        
    </stackLayout>    
</page>


<style>
  .page{
    background-color: #e2e2e2;
  } 
  .card{
    background-color: #e9e9e9; 
    animation-name: fade;
    animation-duration: 0.5s;
    animation-fill-mode: forwards;
    animation-timing-function: ease-in;
  } 
  @keyframes fade{
  from{
    opacity: 0.5;
    transform: scale(0.8)
    }
  to{
    opacity: 1;
    transform: scale(1)
    }
  }
  
  .buttonsMain{
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0;
    background-color: rgb(0, 0, 0);
  }
  
  .buttonsMain > button{
    margin: 15 15;
    background-color: rgb(0, 0, 0);
    color: whitesmoke;
  }
  .stackTwo > image {
    width: 80;
    height: 80;
  }
  
  .stackTwo{
    justify-content: center;
    align-items: center;
  } 
  .line{
   width: 50%;
   height: 1;
   background-color: white;
   margin: 15;
  }
  .h1{
    font-size: 23;
  }
  .p{
    font-size: 15;
  }
    
</style>