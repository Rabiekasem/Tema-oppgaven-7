<script>
  import {navigate} from "svelte-native"
  import {showModal} from "svelte-native"
  import News from "./pages/News.svelte"
  import Games from "./pages/Games.svelte"
  import SubPage3 from "./modals/SubPage3.svelte"
  import SubPage4 from "./modals/SubPage4.svelte" 

    
  const showNews = async() =>{
        await navigate({
            page: News,
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

  const lebronArticle = async() =>{
        await showModal({
            page: SubPage3,
            fullscreen: "true",
            props:{
                msg:""
            }
        })
  } 
  const goatArticle = async() =>{
        await showModal({
            page: SubPage4,
            fullscreen: "true",
            props:{
                msg:""
            }
        })
  }
 
</script>


<page class="page" actionBarHidden={true}>
    <scrollView class="scroll">
        <stackLayout>
    
            <stackLayout>
                <flexboxLayout class="buttonsMain" alignItems="flex-start" backgroundColor="">
        	        <button text="Main" width="70" height="30" backgroundColor=""/>
        	        <button text="News" width="70" height="30" backgroundColor="" on:tap={() => showNews()}/>
        	        <button text="Games" width="70" height="30" backgroundColor="" on:tap={() => showGames()}/>
                </flexboxLayout>
            </stackLayout>
        
            <stackLayout>
                <image class="stack2" src="https://7wallpapers.net/wp-content/uploads/2016/05/20_Lebron-James.jpg"
                stretch="none" />
                <image class="logoImg" src="https://i.imgur.com/PLIvCSw.png"
                stretch="fill" />
            </stackLayout>
    
            
            <stackLayout class="stack3" on:tap={() => lebronArticle()} >
                <label class="label1" textwrap={true} text="LeBron's Physique Desirable!" />
                <label class="label2" text="Click to read" textDecoration="Underline"/>
                <label class="label3" textwrap={true} text="Lebron James is one of the best examples of that muscular, but lean physique that we talk about all the time" />
            </stackLayout>

            <stackLayout>
               <dockLayout stretchLastChild="true" backgroundColor="#3c495e">
                    <image class="dockImg" height="300" width="125" src="~/images/lebron1.jpg"
                    stretch="aspectFill" /> 
	                <image class="dockImg" height="300" width="125" src="~/images/lebron2.jpg"
                    stretch="fill" />
                    <image class="dockImg" height="300" src="~/images/lebron3.jpg"
                    stretch="fill" />
               </dockLayout>
            </stackLayout>

            <stackLayout class="stack5" on:tap={() => goatArticle()}>
                <label class="label1" textwrap={true} text="The Ultimate NBA G.O.A.T. Debate" />
                <label class="label2" text="Click to read" textDecoration="Underline"/>
                <label class="label3" textwrap={true} text="LeBron James continues to build his legacy as one of the greatest NBA athletes ever...but is he the greatest player of all time? It's a debate that has raged between NBA fans for years. Jordan is revered as the greatest because of his killer instinct and championship pedigree. James has accomplished more statistically at this point in his career and may be the more imposing athlete. But who is the 🐐 ? 🏀" />
            </stackLayout>

            <stackLayout>
                <flexboxLayout flexDirection="column" backgroundColor="#3c495e">
	                <image height="100" width="100%" src="~/images/jordan.jpg"
                    stretch="aspectFill" /> 
	                <image height="100" width="100%" src="~/images/braynt.jpg"
                    stretch="fill" />
                    <image height="100" src="~/images/james.jpg"
                    stretch="fill" />
                </flexboxLayout>
            </stackLayout>
    
        </stackLayout>
    </scrollView>
</page>



<style>
 .scroll{
    background-color: #e2e2e2;
 } 

 .buttonsMain{
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0;
    background-color: rgb(0, 0, 0);

    animation-name: leftIn;
    animation-duration: 0.5s;
    animation-fill-mode: forwards;
    animation-timing-function: ease-in;
 }

 .buttonsMain > button{
    margin: 15 15;
    background-color: rgb(0, 0, 0);
    color: whitesmoke;
 }

 .stack2{
    animation-name: fadeToLeft;
    animation-duration: 0.5s;
    animation-fill-mode: forwards;
    animation-timing-function: ease-in;
    position: relative;
    top: 0;
    left: 0;
    background-attachment: fixed;
 }

 .stack3, .stack5{
     margin: 0 15;
     margin-top: 40;
     margin-bottom: 20;
 }


 .logoImg{
    animation-name: fadeToRight;
    animation-duration: 0.5s;
    animation-fill-mode: forwards;
    animation-timing-function: ease-in;
    position: absolute;
    width: 110;
    height: 90;
    margin-top: -45;
 }

 .label1{
    font-weight: 600;
    font-size: 40;
    margin-top: 20;
 }

 @keyframes leftIn{
    from { transform: translateY(-100); }
    to { transform: translateY(0); }
 }
 @keyframes fadeToLeft{
    from { transform: translateX(-100); }
    to { transform: translateX(0); }
 }
 @keyframes fadeToRight{
    from { transform: translateX(100); }
    to { transform: translateX(0); }
 }

</style>
