<script>
// @ts-nocheck



// @ts-nocheck

     // @ts-ignore
     export let data;
     export let char;
    
     console.log(data.lenth);

</script>


{#each data as datas}
    <div class='blog_box'>
        <div class='blog_head_box'>
            <p class='blog_head'>{datas.blogtitle}</p>
        </div>
        <img src='/uploads/post/angularlogo.png' alt="" class='blog_img'/>
        <div class='blog_sub_box'>
            <p class='blog_sub'>{datas.blogsubject}</p>
            <img src="/uploads/profile/download.png" alt="" class='auther_profile'/>
            <p class='blog_auther'>name</p>
        </div>

        <div class='blog_content_box'>
            <p class='blog_content'>{datas.blogcontent.slice(0,`${char}`)}</p>
        </div>
    </div>
{/each}

<style>
    .blog_box{
    width: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 1.5rem;
    border-radius: 10px;
    padding: .5rem 0;
    background: wheat;
    box-shadow: 0px 2px 13px 0px rgba(0,0,0,0.75);
}
    /* blog images */
    .blog_img{
        width: 85%;
        height: 15rem;
        border-radius: 12px;
        margin-top: 1rem;
        box-shadow: 0px 2px 13px 0px rgba(0,0,0,0.75);
    }

    /* blog subject , heading,content */

    .blog_sub_box,.blog_head_box,
    .blog_content_box{
        width: 90%;
        display: flex;
        justify-content: start;
        align-items: center;
        margin-top: 1rem;
    }
    .blog_sub{
        font-size: 14px;
        font-family: work sans;
        text-decoration: underline;
    }
    .blog_sub_box .auther_profile{
        width: 2.3rem;
        height: 2.3rem;
        border-radius: 50%;
        margin-left: auto;
        margin-right: 2px;
        box-shadow: 0px 2px 13px 0px rgba(0,0,0,0.75);
    }
    .blog_auther{
        font-size: 12px;
        font-weight: 500;
        font-family: sans-serif;
        text-transform: capitalize;
    }

    /* blog head */

    .blog_head{
        font-size: 18px;
        font-family: work sans;
        font-weight: bolder;
    }

    /* BLog content */

    .blog_content{
        font-size: 16px;
        font-family: work sans;
        font-weight: 500;
        text-align: justify;
        margin-top: -.3rem;
    }
</style>