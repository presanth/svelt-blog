<script>

    import uuid from 'react-uuid'

    let id = uuid().slice(0,3)
    console.log(id);

    let res =  [];
    let name = ''
    let email =''
    let password = ''
   // @ts-ignore
     $: file = [];
    const onFileSelected =(e)=>{
        let image = e.target.files[0];
        file = image
    }

    async function Signup(){
        const formData = new FormData() 
        formData.append('id',id)
        formData.append('username',name)
        formData.append('useremail',email)
        formData.append('userpassword',password)
        formData.append('file',file)
        try{
        const result = await fetch('http://localhost:8000/blog/register',{
            method: 'POST',
            headers: {
            'Content-Type': 'application/json',
            },
            body: JSON.stringify(formData),
        })
        res = await result.json();
        console.log(res);
    }catch(error){
        console.log(error ,"erterterr");
    }
    }
</script>

<div class='registration_box'>
    <p class='r_head'>Register</p>
    <form on:submit={Signup}>
        <input type="text" placeholder='name' bind:value={name} />
        <input type="text" placeholder='email' bind:value={email}/>
        <input type="text" placeholder='password' bind:value={password}/>
        <input type="file" class='custom-file-input' on:change={(e)=>onFileSelected(e)}/>
        <button class='register_btn' >submit</button>
    </form>
    
</div>

<style>
    .registration_box{
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .r_head{
        font-size: 25px;
        font-family: work sans;
        font-weight: 600;
    }
    .registration_box input{
        width: 70%;
        height: 2.6rem;
        margin-top: 1rem;
        border-radius: 10px;
        border: 2px solid rgb(0, 167, 95);
        text-align: center;
        padding-left: 1rem;
        font-size: 17px;
        font-family: work sans;
        font-weight: bold;
        color: gray;
    }
    .registration_box input::placeholder{
        font-size: 17px;
        font-family: work sans;
        font-weight: bold;
        text-transform: capitalize;
    }
    .custom-file-input{
        border: none !important;
        padding-top: 8px;
    }
    .custom-file-input::-webkit-file-upload-button {
        visibility: hidden;
    }
    .custom-file-input::before {
        content: 'Add Profile pictuer';
        cursor: pointer;
        background: #009b4e;
        padding: 3px 8px;
        border-radius: 10px;
        color: white;
        padding: 9px 5px;
    }
    .register_btn{
        width: 200px;
        margin-top: 2rem;
        height: 2rem;
        border-radius: 10px;
        outline: none;
        font-family: work sans;
        font-weight: bold;
        font-size: 18px;
        text-transform: capitalize;
        border: 2px solid #009e6f;
        background: #009b4e;
        color: white;
    }
</style>