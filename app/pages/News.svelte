<script>
  import {onMount} from "svelte"
  import {goBack} from "svelte-native"
  import {navigate} from "svelte-native"
  import {showModal} from 'svelte-native'
  import Games from "./Games.svelte"
  import App from "../App.svelte"
  import SubPage from "../modals/SubPage.svelte"
  
  const apiKey = "e14f4ede420e450baafed861c6893a83"
  const NewsApi = `https://newsapi.org/v2/top-headlines?sources=bbc-news&apiKey=${apiKey}`
  
  import { registerNativeViewElement } from 'svelte-native/dom'
    registerNativeViewElement("cardView", () => 
      require("@nstudio/nativescript-cardview").CardView
    )
  
  let articles = []
  
  const showMain = async() =>{
    await navigate({
      page: App,
      props:{
        msg:""
      }
    })
  }
  const showGames = async() =>{
    await navigate({
      page: Games,
      props:{
        msg:""
      }
    })
  }

  const showPage = async(article) =>{
    await showModal({
      page: SubPage,
      fullscreen: true,
      props:{
        article:article
      }
    })
  }

  const articleSearch = async() =>{
    await showModal({
      page: ArticleSearchPage,
      props:{
        articles:articles
      }
    })
  }
  
  onMount (() => {
    console.log("HELLO HELLO")
    fetch(NewsApi)
    .then(response => response.json())
    .then(json => {
      console.log("HELLO HELLO", json)
      articles = json.articles
      })
    .catch(error => console.log(error))
  })

</script>


<page class="page" actionBarHidden={true}>
  <stackLayout>
      <stackLayout class="stackStack">
        <flexboxLayout class="buttonsMain" alignItems="flex-start" backgroundColor="">
    	    <button text="Main" width="70" height="30" backgroundColor="" on:tap={() => showMain()}/>
    	    <button text="News" width="70" height="30" backgroundColor=""/>
    	    <button text="Games" width="70" height="30" backgroundColor="" on:tap={() => showGames()}/>
        </flexboxLayout>
      </stackLayout>
    
      <stackLayout>
          <scrollView height="100%">
            <stackLayout class="articles" >
              {#each articles as article}
                <cardView class="card" elevation="100" margin="25" height="210" width="90%">
                  <flexboxLayout class="article" height="100%" flexDirection="row"  on:tap={() => showPage(article)}>
                      <image src="{article.urlToImage}" class="img-rounded img" stretch="fill" />
                      <stackLayout class="lastStack" height="100%">
                        <label textWrap={true} class="p text-center" text ="{article.title}" />
                        <label text ="{article.author}" class=" p author text-center"/>
                      </stackLayout>
                  </flexboxLayout>
                </cardView>
                <label class="line"/>
              {:else}    
                <activityIndicator busy="{true}" />
              {/each}
            </stackLayout> 
          </scrollView>
      </stackLayout>
  </stackLayout>
</page>


<style>

  .page{
    background-color: #e2e2e2;
  }  

  .card{
      background-color: #e9e9e9;
    }

    .p{
      margin-left: 12;
    }

  .buttonsMain{
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0;
    background-color: rgb(0, 0, 0);

  }  
  .buttonsMain > button{
    background-color: rgb(0, 0, 0);
    margin: 15 15;
    color: whitesmoke;
     
  }  
  .article{
    padding: 10;
    margin: 10;
    color: black;
    max-height: 100;
    width: 90%;
    border-radius: 10%;

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
  .articles{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
  }
  .line{
    width: 80%;
    height: 1;
    background-color: white;
    margin: 15;
  }
  .img{
    width: 280;
  }
  
  .author{
    bottom: 0;
    font-size: 10;
    
    color: rgb(128, 87, 124);
    font-size: 18;
  }
  .lastStack{
    margin: 20 auto;
  }

</style>