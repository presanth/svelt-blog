<script>
    import {goto} from '$app/navigation'
    let name = ''
    let password = ''
    /**
     *     @type{any}
     */
    $: res = [];

    async function login(){
        const body = {
        name,
        password
    }
        console.log(name);
        const result = await fetch('http://localhost:8000/blog/userLogin',{
            method:'POST',
            headers: {
            'Content-Type': 'application/json',
            },
            body:JSON.stringify(body)
        })
        
        res = await result.json();
        console.log(res);
        if(res.message == "login success"){
        localStorage.setItem("userid",JSON.stringify(res.data.id))
        console.log(res.data);
        // window.location.href = '/Home';
        goto('/Home')
        alert(res.message);
      }else{
        alert(res.message)
      }
    }

</script>

<div class='login_box'>
    <p class='r_head'>SignIn</p>
    <input type="text" placeholder='email' bind:value={name}/>
    <input type="text" placeholder='Password' bind:value={password}/>
    <button class='login_btn' type="button" on:click={login}>submit</button>
</div>

<style>
    .login_box{
        width: 100%;
        height: 20rem;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .login_box input{
        width: 70%;
        height: 2.6rem;
        margin-top: 1.5rem;
        border-radius: 10px;
        outline: none;
        border: 1.7px solid rgb(0, 79, 182);
        padding-left: 1rem;
        text-align: center;
        font-size: 17px;
        font-family: work sans;
        font-weight: bold;
        color: gray;
    }
    .login_box input::placeholder{
        font-size: 17px;
        font-family: work sans;
        text-transform: capitalize;
        font-weight: bold;
    }

    .login_btn{
        width: 200px;
        margin-top: 2rem;
        height: 2rem;
        border-radius: 10px;
        outline: none;
        font-family: work sans;
        font-weight: bold;
        font-size: 18px;
        text-transform: capitalize;
        border: 2px solid rgb(0, 132, 147);
        background: #005dba;
        color: white;
    }
</style>