
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

    const lebronArticle = async() =>{
        await showModal({
            page: SubPage3,
            fullscreen: "true",
            props:{
                msg:"hi"
            }
        })
    }

    const goatArticle = async() =>{
        await showModal({
            page: SubPage4,
            fullscreen: "true",
            props:{
                msg:"hi"
            }
        })
    }

    
</script>


<page class="page" actionBarHidden={true}>
    <scrollView>
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
                       <image class="dockImg" height="300" width="125" src="https://www.nba.com/lakers/sites/lakers/files/ww-04-bronfor3.jpg"
                       stretch="aspectFill" /> 
	                   <image class="dockImg" height="300" width="125" src="https://i.pinimg.com/236x/45/76/5e/45765e1cb8d69e40a47f782b85b92198.jpg"
                       stretch="fill" />
                       <image class="dockImg" height="300" src="https://fsb.zobj.net/crop.php?r=7Sv8DzGZx-kW-mk6VZTV0O3hWRBHn7K1u57vHk1a-PS92WxydejDyqOx7rIbxWglCVrwfqKpyIL1sfLAew6RgjhCrV6UZ-Z7O_rOX_5LZb03vvWzy75vDW1mTQ8YGVQ6gJM3cYWJsWRfR9J5"
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
	                <image height="100" width="125" src="https://lh3.googleusercontent.com/proxy/BEEXdULOCAMtwB4LaoVzn7X4x51TgANJ1Lhx2PObrq5c17vY4KQbB6c5CE1NJbebEiyi_BE6aOs_3OFyInJL2mKbkkAYTpscMVMj3kMmEE8wZATqhyAYY5e90xoxMaVJ2a6q6UYx-ccZX1bkShfjpkEf-cepj6Fdzlk_Z_F06A"
                    stretch="aspectFill" /> 
	                <image height="100" width="125" src="https://pbs.twimg.com/media/EPPW00zW4AQCDR-.jpg"
                    stretch="fill" />
                    <image height="100" src="https://lh3.googleusercontent.com/proxy/g0zh0LHGuXKHFaBI3CSrXlg-n43wevfDYngd94ezuVss1fI8_nxGnPQiNE88eiPS1g_FiEe7zdOBm8TeepgWXh6xFoObFNphM01cRVwu0tSGuQtW85w-E1iEtnDV_V_tRTanqKGMWkEBIaDLbV1N7qTNo0vWaH053AwsR_aHsPhOeg"
                    stretch="fill" />
                </flexboxLayout>
            </stackLayout>
    
        </stackLayout>
    </scrollView>
    
    
</page>



<style>
 .page{
    background-color: white;
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
