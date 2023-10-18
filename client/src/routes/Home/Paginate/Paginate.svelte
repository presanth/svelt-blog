<script>
    import { onMount } from "svelte";
    export let totalPost
    export let postPerPage

    



    const pageNumber = [];
    for(let i=1;i<= Math.ceil(totalPost / postPerPage); i++){
        pageNumber.push(i);
    }
    onMount(()=>{
        const page = document.querySelectorAll('.page_item');
        page.forEach((btn,index)=>{
            btn.addEventListener('click',(e)=>{
                page.forEach(btn=>{btn.classList.remove('active')});
                btn.classList.add('active')
            })
        })
    })


</script>


<div class='pagination_bar'>
    <ul class='pagination_bar_sec'>
        {#each pageNumber as p}
        <li class='page_item'></li>
        {/each}
        
    </ul>
</div>


<style>
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
    .page_item.active{
        background: #030111;
        color: white;
    }
</style>