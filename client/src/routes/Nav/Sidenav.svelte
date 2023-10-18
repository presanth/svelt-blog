


<div class='sidenav_main'>
    <p class='side_head'>Blog Box</p>
    <div class='side_list'>
            <a href={'/Home'} class='item_list'><i class="fa-solid fa-house"></i>Home</a>
            <a href={'/CreateBlog'} class='item_list'><i class="fa-solid fa-pen"></i>Write</a>
            <a href={'/User'} class='item_list'><i class="fa-solid fa-user"></i>User</a>
            <a href={'/'}  class='item_list'><i class="fa-solid fa-right-from-bracket"></i>LogOut</a>
    </div>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Work+Sans&display=swap');
    .sidenav_main{
        width: 17%;
        height: 100vh;
        background: #030111;
        border-right: 1px solid rgb(188, 188, 188);
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .side_head{
        font-family: work sans;
        font-size: 20px;
        font-weight: 600;
        margin-top: 2rem;
        color: rgb(17, 180, 255);
    }
    .side_list{
        width: 100%;
        margin-top: 6rem;
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 20rem;
    }
    .side_list .item_list{
        list-style: none;
        margin-top: 1.3rem;
        text-decoration: none;
        font-weight: 600;
        color: #e1e1e1;
        font-family: work sans;
    }
    .side_list .item_list:nth-child(4){
        margin-top: auto;
    }
    .item_list i{
        margin-right: 1rem;
    }

</style>