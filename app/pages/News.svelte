<script>

  import {onMount} from "svelte"
  import {goBack} from "svelte-native"
  import {navigate} from "svelte-native"
  import {showModal} from 'svelte-native'
  import Games from "./Games.svelte"
  import App from "../App.svelte"
  import SubPage from "../modals/SubPage.svelte"
  
  const apiKey = "e14f4ede420e450baafed861c6893a83"
  const NewsApi = `https://newsapi.org/v2/everything?q=apple&from=2020-03-30&to=2020-03-30&sortBy=popularity&apiKey=${apiKey}`
  
  
  
  let articles = []
  
  const showMain = async() =>{
      await navigate({
          page: App,
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
          <stackLayout>
              <flexboxLayout class="buttonsMain" alignItems="flex-start" backgroundColor="">
      	        <button text="Main" width="70" height="30" backgroundColor="" on:tap={() => showMain()}/>
      	        <button text="News" width="70" height="30" backgroundColor=""/>
      	        <button text="Games" width="70" height="30" backgroundColor="" on:tap={() => showGames()}/>
              </flexboxLayout>
          </stackLayout>
      
          <stackLayout>
              <scrollView>
                  <stackLayout class="articles" >
                    {#each articles as article}
                        <flexboxLayout class="article" flexDirection="row"  on:tap={() => showPage(article)}>
                            <image src="{article.urlToImage}" class="img-rounded img" stretch="fill" />
                            <stackLayout class="lastStack">
                                <label textWrap={true} class="p text-center" text ="{article.title}" />
                                <label text ="{article.author}" class=" p text-center author"/>
                            </stackLayout>
                        </flexboxLayout>
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
     background-color: brown;
  }  

  .buttonsMain{
     display: flex;
     align-items: center;
     justify-content: center;
     padding: 0;
     background-color: rgb(95, 48, 48);
  }  
  .buttonsMain > button{
     background-color: rgb(95, 48, 48);
     margin: 15 15;
     color: aliceblue;
     
  }  
  .article{
     background-color: rgb(206, 206, 206);
     padding: 10;
     margin: 10;
     color: black;
     max-height: 100;
     width: 90%;
     border-radius: 10%;
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
     margin: 0;
     width: 250;
     height: 130;
  }
  .author{
     bottom: 0;
     right: 0;
     font-size: 10;
     padding-top: 50;
     color: rgb(128, 87, 124);
     font-size: 18;
  }
  
</style>