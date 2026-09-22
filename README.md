# bookclubsunited
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport"
      content="width=device-width, initial-scale=1.0,
               maximum-scale=1.0,user-scalable=no">

<title>BookClubsUnited</title>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
:root{
    --espresso:#3b2118;
    --coffee:#6f4532;
    --latte:#a87554;
    --cream:#f7efe4;
    --paper:#fffaf3;
    --foam:#ffffff;
    --muted:#8b7568;
    --border:#e5d5c6;
    --danger:#9b4035;
}

*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

body{
    font-family:Georgia,"Times New Roman",serif;
    background:var(--cream);
    color:var(--espresso);
    min-height:100vh;
}

button,input,textarea{
    font:inherit;
}

button{
    cursor:pointer;
}

.hidden{
    display:none!important;
}

/* =========================
   HEADER
========================= */

header{
    position:sticky;
    top:0;
    z-index:20;

    background:rgba(59,33,24,.97);
    color:white;

    padding:14px 20px;

    display:flex;
    align-items:center;
    justify-content:space-between;

    box-shadow:0 3px 15px rgba(0,0,0,.18);
}

.logo{
    font-size:22px;
    font-weight:bold;
    letter-spacing:.5px;
}

.logo small{
    display:block;
    font-size:10px;
    font-weight:normal;
    opacity:.65;
    letter-spacing:1px;
}

.header-actions{
    display:flex;
    gap:8px;
}

.icon-btn{
    border:0;
    background:#ffffff18;
    color:white;
    width:40px;
    height:40px;
    border-radius:50%;
    font-size:21px;
}

/* =========================
   AUTH
========================= */

#authScreen{
    min-height:100vh;
    display:flex;
    align-items:center;
    justify-content:center;
    padding:25px;
}

.auth-card{
    width:100%;
    max-width:420px;
    background:var(--paper);
    border:1px solid var(--border);
    border-radius:24px;
    padding:32px;
    box-shadow:0 12px 40px rgba(59,33,24,.12);
}

.auth-logo{
    text-align:center;
    font-size:30px;
    font-weight:bold;
    margin-bottom:5px;
}

.auth-tag{
    text-align:center;
    color:var(--muted);
    font-size:12px;
    margin-bottom:30px;
}

.auth-card h2{
    margin-bottom:18px;
}

.field{
    margin-bottom:15px;
}

.field label{
    display:block;
    margin-bottom:6px;
    font-size:13px;
}

.field input,
.field textarea{
    width:100%;
    padding:12px 14px;
    border:1px solid var(--border);
    border-radius:12px;
    background:white;
    color:var(--espresso);
    outline:none;
}

.field input:focus,
.field textarea:focus{
    border-color:var(--latte);
}

.primary{
    width:100%;
    padding:13px;
    border:0;
    border-radius:12px;
    background:var(--coffee);
    color:white;
    font-weight:bold;
}

.switch-auth{
    text-align:center;
    margin-top:18px;
    font-size:13px;
}

.switch-auth button{
    border:0;
    background:none;
    color:var(--coffee);
    font-weight:bold;
}

/* =========================
   APP
========================= */

#app{
    min-height:100vh;
}

.layout{
    max-width:1100px;
    margin:auto;
    display:grid;
    grid-template-columns:220px minmax(0,1fr) 220px;
    gap:20px;
    padding:25px 15px;
}

.sidebar,
.rightbar{
    position:sticky;
    top:85px;
    height:max-content;
}

.panel{
    background:var(--paper);
    border:1px solid var(--border);
    border-radius:18px;
    padding:17px;
    margin-bottom:15px;
}

.panel h3{
    font-size:15px;
    margin-bottom:13px;
}

.nav-btn{
    width:100%;
    text-align:left;
    border:0;
    background:none;
    padding:10px;
    border-radius:10px;
    color:var(--espresso);
    margin-bottom:4px;
}

.nav-btn:hover{
    background:#eadacc;
}

.feed-title{
    font-size:25px;
    margin-bottom:18px;
}

.post{
    background:var(--paper);
    border:1px solid var(--border);
    border-radius:20px;
    overflow:hidden;
    margin-bottom:20px;
    box-shadow:0 5px 18px rgba(59,33,24,.06);
}

.post-head{
    display:flex;
    align-items:center;
    gap:10px;
    padding:15px;
}

.avatar{
    width:42px;
    height:42px;
    border-radius:8px;
    object-fit:cover;
    background:#dbc4b2;
}

.avatar.large{
    width:55px;
    height:55px;
}

.username{
    font-weight:bold;
}

.date{
    color:var(--muted);
    font-size:11px;
}

.post-content{
    padding:0 15px 15px;
}

.post-title{
    font-size:23px;
    margin-bottom:8px;
}

.synopsis{
    color:#624e43;
    line-height:1.55;
    font-size:14px;
}

.thumbnail{
    width:100%;
    aspect-ratio:16/9;
    object-fit:cover;
    display:block;
    background:#e4d2c1;
}

.read-btn{
    margin-top:15px;
    border:0;
    background:var(--coffee);
    color:white;
    padding:10px 18px;
    border-radius:10px;
    font-weight:bold;
}

.post-actions{
    display:flex;
    border-top:1px solid var(--border);
}

.action{
    flex:1;
    padding:12px 5px;
    border:0;
    background:none;
    color:var(--coffee);
    font-size:13px;
}

.action:hover{
    background:#f0e3d7;
}

/* =========================
   FLOATING PLUS
========================= */

.plus{
    position:fixed;
    right:25px;
    bottom:25px;

    width:58px;
    height:58px;

    border-radius:50%;
    border:0;

    background:var(--espresso);
    color:white;

    font-size:31px;

    box-shadow:0 8px 25px rgba(59,33,24,.3);
}

/* =========================
   MODAL
========================= */

.modal{
    position:fixed;
    inset:0;
    z-index:50;

    background:rgba(20,12,8,.65);

    display:flex;
    align-items:center;
    justify-content:center;

    padding:20px;
}

.modal-card{
    width:100%;
    max-width:500px;
    max-height:90vh;
    overflow:auto;

    background:var(--paper);
    border-radius:22px;
    padding:25px;
}

.modal-head{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:20px;
}

.close{
    border:0;
    background:none;
    font-size:25px;
}

.file-box{
    border:2px dashed var(--border);
    border-radius:15px;
    padding:20px;
    text-align:center;
    margin-bottom:15px;
}

.file-box input{
    margin-top:10px;
    width:100%;
}

/* =========================
   MOBILE
========================= */

@media(max-width:850px){

    .layout{
        display:block;
        max-width:650px;
    }

    .sidebar,
    .rightbar{
        display:none;
    }

    .feed-title{
        margin-top:5px;
    }
}

@media(max-width:500px){

    header{
        padding:12px;
    }

    .logo{
        font-size:18px;
    }

    .layout{
        padding:15px 8px;
    }

    .post-title{
        font-size:20px;
    }

    .plus{
        right:18px;
        bottom:18px;
    }
}
</style>
</head>

<body>

<!-- =========================
     AUTH SCREEN
========================= -->

<section id="authScreen">

<div class="auth-card">

    <div class="auth-logo">
        BookClubsUnited
    </div>

    <div class="auth-tag">
        #zaheenproduct
    </div>

    <div id="loginBox">

        <h2>Welcome back</h2>

        <div class="field">
            <label>Username</label>
            <input id="loginUsername"
                   autocomplete="username"
                   placeholder="Your username">
        </div>

        <div class="field">
            <label>Password</label>
            <input id="loginPassword"
                   type="password"
                   autocomplete="current-password"
                   placeholder="Your password">
        </div>

        <button class="primary"
                onclick="login()">
            Log in
        </button>

        <div class="switch-auth">
            New reader?
            <button onclick="showSignup()">
                Create account
            </button>
        </div>

    </div>


    <div id="signupBox" class="hidden">

        <h2>Create account</h2>

        <div class="field">
            <label>Username</label>
            <input id="signupUsername"
                   autocomplete="username"
                   placeholder="Choose a username">
        </div>

        <div class="field">
            <label>Display name</label>
            <input id="signupDisplayName"
                   placeholder="Your name">
        </div>

        <div class="field">
            <label>Password</label>
            <input id="signupPassword"
                   type="password"
                   autocomplete="new-password"
                   placeholder="Create a password">
        </div>

        <button class="primary"
                onclick="signup()">
            Create account
        </button>

        <div class="switch-auth">
            Already have an account?
            <button onclick="showLogin()">
                Log in
            </button>
        </div>

    </div>

</div>

</section>


<!-- =========================
     APP
========================= -->

<section id="app" class="hidden">

<header>

    <div class="logo">
        BookClubsUnited
        <small>#zaheenproduct</small>
    </div>

    <div class="header-actions">
        <button class="icon-btn"
                onclick="showGroups()">
            👥
        </button>

        <button class="icon-btn"
                onclick="logout()">
            ↪
        </button>
    </div>

</header>


<div class="layout">

    <!-- LEFT -->

    <aside class="sidebar">

        <div class="panel">

            <h3>☕ Library</h3>

            <button class="nav-btn"
                    onclick="showFeed()">
                🏠 Read Feed
            </button>

            <button class="nav-btn"
                    onclick="showGroups()">
                👥 Groups
            </button>

            <button class="nav-btn"
                    onclick="showProfile()">
                👤 My Profile
            </button>

        </div>

    </aside>


    <!-- CENTER -->

    <main>

        <h1 class="feed-title">
            Read Feed
        </h1>

        <div id="feed"></div>

    </main>


    <!-- RIGHT -->

    <aside class="rightbar">

        <div class="panel">

            <h3>☕ BookClubsUnited</h3>

            <p style="font-size:13px;line-height:1.5;color:var(--muted)">
                A place for readers to discover stories,
                share ideas and build book clubs.
            </p>

        </div>

        <div class="panel">

            <h3>Quick links</h3>

            <button class="nav-btn"
                    onclick="showGroups()">
                Find groups
            </button>

            <button class="nav-btn"
                    onclick="openUpload()">
                Upload a story
            </button>

        </div>

    </aside>

</div>


<button class="plus"
        onclick="openUpload()">
    +
</button>

</section>


<!-- =========================
     UPLOAD MODAL
========================= -->

<div id="uploadModal"
     class="modal hidden">

<div class="modal-card">

    <div class="modal-head">

        <h2>Publish a story</h2>

        <button class="close"
                onclick="closeUpload()">
            ×
        </button>

    </div>

    <div class="field">

        <label>Story title</label>

        <input id="storyTitle"
               placeholder="Enter the title">

    </div>

    <div class="field">

        <label>Synopsis / Prologue / Trailer</label>

        <textarea id="storySynopsis"
                  rows="5"
                  placeholder="Tell readers about the story...">
        </textarea>

    </div>

    <div class="file-box">

        <div>
            📄 Upload story file
        </div>

        <input id="storyFile"
               type="file"
               accept=".pdf">

    </div>

    <div class="field">

        <label>Thumbnail</label>

        <input id="storyThumbnail"
               type="file"
               accept="image/*">

    </div>

    <button class="primary"
            onclick="publishStory()">
        Publish
    </button>

</div>
</div>


<script>

/* ==================================================
   SUPABASE CONFIGURATION
================================================== */

const SUPABASE_URL =
    "https://yagbxqixnxwnglusgeah.supabase.co";

const SUPABASE_PUBLISHABLE_KEY =
    "PASTE_YOUR_PUBLISHABLE_KEY_HERE";

const supabaseClient =
    window.supabase.createClient(
        SUPABASE_URL,
        SUPABASE_PUBLISHABLE_KEY
    );


/* ==================================================
   AUTH UI
================================================== */

function showSignup(){

    document.getElementById("loginBox")
        .classList.add("hidden");

    document.getElementById("signupBox")
        .classList.remove("hidden");
}

function showLogin(){

    document.getElementById("signupBox")
        .classList.add("hidden");

    document.getElementById("loginBox")
        .classList.remove("hidden");
}


/* ==================================================
   SIGNUP
================================================== */

async function signup(){

    const username =
        document.getElementById("signupUsername")
        .value.trim()
        .toLowerCase();

    const displayName =
        document.getElementById("signupDisplayName")
        .value.trim();

    const password =
        document.getElementById("signupPassword")
        .value;

    if(!username || !displayName || !password){

        alert("Please fill everything in.");
        return;
    }

    if(username.length < 3){

        alert("Username must be at least 3 characters.");
        return;
    }

    if(password.length < 6){

        alert("Password must be at least 6 characters.");
        return;
    }

    /*
       IMPORTANT:
       Username-only authentication needs an internal
       identifier because Supabase password authentication
       uses email/password underneath.

       We generate an internal email-like identifier.
       The user never needs to see or use it.
    */

    const internalEmail =
        username + "@bookclubsunited.local";


    const {data,error} =
        await supabaseClient.auth.signUp({

            email:internalEmail,

            password:password,

            options:{
                data:{
                    username:username,
                    display_name:displayName
                }
            }

        });


    if(error){

        alert(error.message);
        return;
    }


    alert("Account created!");

    await loadUser();

}


/* ==================================================
   LOGIN
================================================== */

async function login(){

    const username =
        document.getElementById("loginUsername")
        .value.trim()
        .toLowerCase();

    const password =
        document.getElementById("loginPassword")
        .value;

    if(!username || !password){

        alert("Enter your username and password.");
        return;
    }


    const internalEmail =
        username + "@bookclubsunited.local";


    const {data,error} =
        await supabaseClient.auth.signInWithPassword({

            email:internalEmail,

            password:password

        });


    if(error){

        alert("Login failed: " + error.message);
        return;
    }


    await loadUser();
}


/* ==================================================
   LOAD USER
================================================== */

async function loadUser(){

    const {
        data:{session}
    } =
        await supabaseClient.auth.getSession();


    if(!session){

        document.getElementById("authScreen")
            .classList.remove("hidden");

        document.getElementById("app")
            .classList.add("hidden");

        return;
    }


    document.getElementById("authScreen")
        .classList.add("hidden");

    document.getElementById("app")
        .classList.remove("hidden");


    await loadFeed();
}


/* ==================================================
   LOGOUT
================================================== */

async function logout(){

    await supabaseClient.auth.signOut();

    document.getElementById("app")
        .classList.add("hidden");

    document.getElementById("authScreen")
        .classList.remove("hidden");

}


/* ==================================================
   FEED
================================================== */

async function loadFeed(){

    const feed =
        document.getElementById("feed");

    feed.innerHTML =
        "<p style='color:#8b7568'>Loading stories...</p>";


    const {data,error} =
        await supabaseClient

        .from("posts")

        .select(`
            *,
            profiles (
                username,
                display_name,
                avatar_url
            )
        `)

        .order("created_at",{
            ascending:false
        });


    if(error){

        feed.innerHTML =
            "<p>Could not load the feed.</p>";

        console.error(error);

        return;
    }


    if(!data.length){

        feed.innerHTML = `
            <div class="panel">
                <h3>No stories yet.</h3>
                <p style="color:#8b7568">
                    Be the first reader to publish something.
                </p>
            </div>
        `;

        return;
    }


    feed.innerHTML =
        data.map(post => createPostHTML(post))
        .join("");
}


/* ==================================================
   POST CARD
================================================== */

function createPostHTML(post){

    const avatar =
        post.profiles?.avatar_url ||
        "https://placehold.co/100x100/e4d2c1/3b2118?text=📖";


    const username =
        post.profiles?.username ||
        "reader";


    const displayName =
        post.profiles?.display_name ||
        username;


    const date =
        new Date(post.created_at)
        .toLocaleDateString();


    const thumbnail =
        post.thumbnail_url
        ? `<img class="thumbnail"
                src="${escapeHTML(post.thumbnail_url)}">`
        : "";


    return `

    <article class="post">

        <div class="post-head">

            <img class="avatar"
                 src="${escapeHTML(avatar)}">

            <div>

                <div class="username">
                    ${escapeHTML(displayName)}
                </div>

                <div class="date">
                    @${escapeHTML(username)}
                    · ${date}
                </div>

            </div>

        </div>

        ${thumbnail}

        <div class="post-content">

            <h2 class="post-title">
                ${escapeHTML(post.title)}
            </h2>

            <p class="synopsis">
                ${escapeHTML(post.synopsis || "")}
            </p>

            ${
                post.story_file_url
                ?
                `<button class="read-btn"
                         onclick="readStory('${post.id}')">
                    📖 Read it
                </button>`
                :
                ""
            }

        </div>

        <div class="post-actions">

            <button class="action"
                    onclick="react('${post.id}','like')">
                ❤️ Like
            </button>

            <button class="action"
                    onclick="react('${post.id}','dislike')">
                👎 Dislike
            </button>

            <button class="action"
                    onclick="comments('${post.id}')">
                💬 Comment
            </button>

        </div>

    </article>

    `;
}


/* ==================================================
   REACTIONS
================================================== */

async function react(postId,reaction){

    const {
        data:{user}
    } =
        await supabaseClient.auth.getUser();


    if(!user){

        alert("Please log in first.");
        return;
    }


    const {error} =
        await supabaseClient

        .from("post_reactions")

        .upsert({

            post_id:postId,
            user_id:user.id,
            reaction:reaction

        },{
            onConflict:"post_id,user_id"
        });


    if(error){

        console.error(error);
        alert(error.message);
        return;
    }


    alert(
        reaction === "like"
        ? "Liked!"
        : "Disliked!"
    );
}


/* ==================================================
   COMMENTS
================================================== */

async function comments(postId){

    const text =
        prompt("Write your comment:");

    if(!text || !text.trim())
        return;


    const {
        data:{user}
    } =
        await supabaseClient.auth.getUser();


    if(!user)
        return;


    const {error} =
        await supabaseClient

        .from("comments")

        .insert({

            post_id:postId,
            user_id:user.id,
            content:text.trim()

        });


    if(error){

        alert(error.message);
        return;
    }


    alert("Comment posted.");
}


/* ==================================================
   READ STORY
================================================== */

async function readStory(postId){

    const {data:post,error} =
        await supabaseClient

        .from("posts")

        .select("story_file_url,title")

        .eq("id",postId)

        .single();


    if(error || !post?.story_file_url){

        alert("Story could not be opened.");
        return;
    }


    /*
       The story bucket is private.
       Create a temporary signed URL.
    */

    const path =
        extractStoragePath(
            post.story_file_url
        );


    const {data,error:signError} =
        await supabaseClient

        .storage
        .from("stories")
        .createSignedUrl(path,3600);


    if(signError){

        alert(signError.message);
        return;
    }


    window.open(
        data.signedUrl,
        "_blank"
    );
}


/* ==================================================
   UPLOAD
================================================== */

function openUpload(){

    document
        .getElementById("uploadModal")
        .classList.remove("hidden");
}

function closeUpload(){

    document
        .getElementById("uploadModal")
        .classList.add("hidden");
}


async function publishStory(){

    const title =
        document.getElementById("storyTitle")
        .value.trim();

    const synopsis =
        document.getElementById("storySynopsis")
        .value.trim();

    const storyFile =
        document.getElementById("storyFile")
        .files[0];

    const thumbnailFile =
        document.getElementById("storyThumbnail")
        .files[0];


    if(!title){

        alert("Give your story a title.");
        return;
    }


    if(!storyFile){

        alert("Choose a story PDF.");
        return;
    }


    const {
        data:{user}
    } =
        await supabaseClient.auth.getUser();


    if(!user){

        alert("Please log in.");
        return;
    }


    const timestamp =
        Date.now();


    /* STORY */

    const storyPath =
        user.id +
        "/" +
        timestamp +
        "-" +
        safeFileName(storyFile.name);


    const {error:storyError} =
        await supabaseClient

        .storage
        .from("stories")
        .upload(
            storyPath,
            storyFile,
            {
                upsert:false
            }
        );


    if(storyError){

        alert(storyError.message);
        return;
    }


    const storyFileUrl =
        SUPABASE_URL +
        "/storage/v1/object/public/stories/" +
        storyPath;


    /* THUMBNAIL */

    let thumbnailUrl = null;


    if(thumbnailFile){

        const thumbnailPath =
            user.id +
            "/" +
            timestamp +
            "-" +
            safeFileName(thumbnailFile.name);


        const {
            error:thumbnailError
        } =
            await supabaseClient

            .storage
            .from("thumbnails")
            .upload(
                thumbnailPath,
                thumbnailFile,
                {
                    upsert:false
                }
            );


        if(thumbnailError){

            alert(thumbnailError.message);
            return;
        }


        thumbnailUrl =
            SUPABASE_URL +
            "/storage/v1/object/public/thumbnails/" +
            thumbnailPath;
    }


    /* DATABASE POST */

    const {error} =
        await supabaseClient

        .from("posts")

        .insert({

            user_id:user.id,

            title:title,

            synopsis:synopsis,

            thumbnail_url:thumbnailUrl,

            story_file_url:storyFileUrl

        });


    if(error){

        alert(error.message);
        return;
    }


    closeUpload();

    document.getElementById("storyTitle")
        .value="";

    document.getElementById("storySynopsis")
        .value="";

    document.getElementById("storyFile")
        .value="";

    document.getElementById("storyThumbnail")
        .value="";


    await loadFeed();

    alert("Story published!");
}


/* ==================================================
   GROUPS PLACEHOLDER
================================================== */

function showGroups(){

    alert(
        "Groups are connected to the backend. " +
        "The Groups interface is coming in the next build."
    );
}

function showProfile(){

    alert(
        "Profile interface is coming in the next build."
    );
}

function showFeed(){

    loadFeed();
}


/* ==================================================
   HELPERS
================================================== */

function safeFileName(name){

    return name
        .replace(/[^a-zA-Z0-9._-]/g,"_");
}


function escapeHTML(value){

    return String(value ?? "")
        .replace(/&/g,"&amp;")
        .replace(/</g,"&lt;")
        .replace(/>/g,"&gt;")
        .replace(/"/g,"&quot;")
        .replace(/'/g,"&#039;");
}


function extractStoragePath(url){

    const marker =
        "/storage/v1/object/";

    const index =
        url.indexOf(marker);

    if(index === -1)
        return url;

    let path =
        url.substring(
            index + marker.length
        );

    path =
        path.replace(/^public\//,"");

    path =
        path.replace(/^stories\//,"");

    return path;
}


/* ==================================================
   START APP
================================================== */

loadUser();

</script>

</body>
</html>
