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

    const showNba = async() =>{
        await showModal({
            page: SubPage2,
            fullscreen: true,
            props:{
                msg: "hi"
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
    
        <scrollView class="scrollOne">
        <stackLayout class="stackOne">
          {#each items as item}
                    <flexboxLayout class="stackTwo" flexDirection="column" >
                        <image src="{item.fields.IMG}" stretch="aspectFit" on:tap={() => showNba()} />
                        <label class="h1" text={item.fields.teamName}/>
                        <label class="p" text= Win:{item.fields.W}/>
                        <label class="p" text= Lose:{item.fields.L}/>
                        <label class="line"/>
                    </flexboxLayout>
              {:else}
              <activityIndicator busy={true}/>
          {/each}
        </stackLayout>
        </scrollView>
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
        padding: 0;
        background-color: rgb(95, 48, 48);
    }
    
    .buttonsMain > button{
        margin: 15 15;
        background-color: rgb(95, 48, 48);
        color: antiquewhite;
    }
    .stackTwo > image {
        width: 80;
        height: 80;
    }
    
    label{
        font-size: 18;
    }
    .stackTwo{
        justify-content: center;
        align-items: center;
    }
    .line{
     width: 80%;
     height: 1;
     background-color: white;
     margin: 15;
    }
    .h1{
        font-size: 20;
    }
    .p{
        font-size: 15;
    }
</style>