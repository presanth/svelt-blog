<script>
// @ts-nocheck

    import { onMount } from "svelte";
    import Sidenav from "../Nav/Sidenav.svelte";
    import Blog from "../Blog/Blog.svelte";
    import { goto } from "$app/navigation";
    // import Paginate from "./Paginate/Paginate.svelte";
    

    /**
     * @type {never[]}
     */
     let res = [];
     let CurrentPosts = [];
     $: pp = [];

     const postPerpage = 3;
     $:  currentpage = 1;
    

    onMount(
    async function getBlog(){
        const result = await fetch('http://localhost:8000/blog/getAllBlogs')
        res = await result.json();
        console.log(res);

        const indexOfLastPost = currentpage * postPerpage;
        const indexOfFirstPost = indexOfLastPost - postPerpage;
        CurrentPosts = res.slice(indexOfFirstPost,indexOfLastPost); 
        console.log(CurrentPosts);

        let pageNumber = [];
        let totalPost = res.length
        for(let i=1;i<= Math.ceil(totalPost / postPerpage); i++){
        pageNumber.push(i);
        pp = pageNumber
        }
        console.log(pageNumber);
    },
    ()=>{
        const page = document.querySelectorAll('.page_item');
        page.forEach((btn,index)=>{
            btn.addEventListener('click',(e)=>{
                page.forEach(btn=>{btn.classList.remove('active')});
                btn.classList.add('active')
            })
        })
    }
    )

    function paginate(n){
        currentpage=n;
        console.log(currentpage);
    }
    


</script>


<div class='home_container'>
    <Sidenav/>
    <div class='home_content'>
        <div class='search_box'>
            <input type="text" placeholder='Search Content' class='search_inp' />
            <i class="fa-solid fa-magnifying-glass"></i>
        </div>
        <div class='home_blog'>
            <Blog data={CurrentPosts} char={'300'}/>
        </div>
        <div class='home_pagination'>
          <div class='pagination_bar'>
            <ul class='pagination_bar_sec'>
                {#each pp as p}
                    <li class='page_item' on:click={paginate(p)}>{p}</li>
                {/each}    
            </ul>
        </div>
        </div>
        
    </div>
</div>

<style>
    *{
        padding: 0;
        margin: 0;
    }
    .home_container{
        width: 100%;
        height: 100vh;
        display: flex;
    }
    .home_content{
        width: 83%;
        height: 100vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        background: #030111;
    }
    .search_box{
        width: 94%;
        height: 4rem;
        display: flex;
        align-items: center;
        border-bottom: 2px solid rgb(73 73 73);
        margin-top: 1rem;
    }
    .search_inp{
        width: 30%;
        height: 2.5rem;
        border-radius: 20px;
        border: 1px solid black;
        outline: none;
        padding-left: 20px;
        position: relative;
        margin-bottom: 1rem;
    }
    .search_inp::placeholder{
        font-weight: bold;
        font-size: 15px;
    }
    .search_box .fa-magnifying-glass{
        position: absolute;
        color: black;
        margin-left: 21.5rem;
        font-size: 17px;
    }
    .home_blog{
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        overflow: auto;
        
    }
    .home_blog::-webkit-scrollbar{
        display: none;
    }

    .home_pagination{
        width: 83%;
        position: fixed;
        bottom: 7px;

    }


    .pagination_bar{
        width: 100%;
        height: 3rem;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .pagination_bar_sec{
        background: rgb(255, 255, 255);
        border-radius: 60px;
        display: flex;
        justify-content: center;
        list-style: none;
        padding: .3rem 4rem;
    }
    .page_item{
        width: 3rem;
        height: 3rem;
        display: flex;
        justify-content: center;
        align-items: center;
        border: 1px solid gray;
        color: #030111;
        border-radius: 50%;
        cursor: pointer;
        font-size: 18px;
        font-weight: 600;
        margin-right: .5rem;
    }
    .active{
        background: #030111;
        color: white;
    }
</style>