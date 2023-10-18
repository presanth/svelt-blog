<script>
    import { onMount } from "svelte";
    import Login from "./Authenticate/Login.svelte";
    import Register from "./Authenticate/Register.svelte";

    onMount(()=>{
        const tabs = document.querySelectorAll('.tab_btn');
        const all_content = document.querySelectorAll('.tab_content');
    
        tabs.forEach((tab,index)=>{
            tab.addEventListener('click',(e)=>{
                tabs.forEach(tab=>{tab.classList.remove('active')});
                tab.classList.add('active');
                all_content.forEach(content=>{content.classList.remove('active')});
                all_content[index].classList.add('active');
            })
        })
    })

</script>

<div class='main_container'>
    <div class='main_tab_box'>
        <div class='tabs'>
            <button class='tab_btn active'>Login</button>
            <button class='tab_btn'>Register</button>
        </div>
        <div class='tab_content_box'>
            <div class='tab_content active'>
                <Login/>
            </div>
            <div class='tab_content'>
                <Register/>
            </div>
        </div>
    </div>
</div>

<style>
    .main_container{
        width: 100%;
        height: 100vh;
        display: flex;
        justify-content: center;
        background: darkolivegreen;
        margin: 0;
        padding: 0;
    }
    .main_tab_box{
        width: 40%;
        height: 30rem;
        display: flex;
        flex-direction: column;
        background: #fff;
        border-radius: 10px;
        margin-top: 2rem;
    }
    .tabs{
        width: 100%;
        height: 3rem;
        display: flex;
        justify-content: space-around;
        border-bottom: 1px solid rgb(179, 179, 179);
        margin-top: 1rem;
        position: relative;
    }
    .tab_btn{
        width: 45%;
        outline: none;
        border: none;
        background: transparent;
        font-size: 20px;
        font-weight: 600;
        font-family: work sans;
    }
    .tab_btn.active{
        color: rgb(64, 4, 65);
        background: wheat;
        transition: all .3s ease-in-out;
    }
    .tab_content_box{
        width: 100%;
    }
    .tab_content{
        display: none;
    }
    .tab_content.active{
        display: flex;
    }
    .line{
        position: absolute;
        width: 100px;
        height: 5px;
        background: #000;
        left: 100px;
        top: 40px;
        border-radius: 10px;
        transition: all .3s ease-in-out;
    }
</style>