<script>
    import { Router, Route, Link } from "svelte-routing";
    import Home from "./pages/Home.svelte";
    import Mint from "./pages/Mint.svelte";
    import Intel from "./pages/Intel.svelte";
    import Four from "./pages/Four.svelte";
    import Gallery from "./pages/Gallery.svelte"
    export let url = '';
    import { setContext } from 'svelte';
    import { writable } from 'svelte/store';
    import { fade } from 'svelte/transition';
    import { Audio, Video } from 'svelte-audio-video'

  const track = {
    attach: (element, _track) => {
      // when fired, do whatever is needed to attach the track
      // Note: `this` refers to the `track` object
    },
 
    detach: (element, _track) => {
      // when fired, do whatever is needed to detach the track
      // Note: `this` refers to the `track` object
    },
  }
    const app = writable({});
    //export const innerHeight = writable(1000)
    //export const innerWidth = writable(1000) Any use for these
    setContext('app', app);
    console.log(window.location.href);
</script>

<div class="main">
    <Audio controls={false}>
        <source
          src="/"
          type="audio/mp3" />
      </Audio>
	<header>
    <Router url="{url}">
      
      <div class="left-box">
                <Link to="/">
        <h1 class="main-title">GURA</h1></Link>
      </div>

      <nav>
        <Link to="mint"><p style="font-size:1.8rem;margin:0rem 1rem;">Mint</p></Link>
        <Link to="gallery"><p style="font-size:1.8rem;margin:0rem 1rem;">Gallery</p></Link>
        <Link to="intel"><p style="font-size:1.8rem;margin:0rem 1rem;">Intel</p></Link>
      </nav>
    
        <Route path="/"><Home /></Route>
        <Route path="/mint" component={Mint}><Mint /></Route>
        <Route path="/mint"><Mint /></Route>
        <Route path="/intel" component={Intel}><Intel /></Route>
        <Route path="/gallery" component={Gallery}></Route>
        <Route path="/*"><Four /></Route>

    </Router>
    <div class="right-box">
      <div class="mint-button wallet-button"><p>Connect Wallet</p></div>

    </div>
  </header>
    <script type="text/javascript" src="/script.js"></script>
    <footer>
      <div class="footer-text"><p style="display:flex;"><b><i style="margin-right:0.5rem;">GURANFT </i></b> is a <b style="margin-left:0.5rem;margin-right:0.5rem;">GURACORPⓇ</b> Company 2021 · <a href="/intel">Intel</a>· <a href="">Contact</a></p></div>
    </footer>
</div>
<style>
	.main {
		text-align: center;
		padding: 0rem;
		margin: 0 auto;
    
	}
  .main-title{
    transform: scaleX(1.4);
        letter-spacing: 0px;margin-top: 1.5rem;
        margin-bottom: 1.5rem;}
  .left-box{width:220px;display:flex;flex-flow:column;justify-content: center;}
  .right-box{width:220px;display:flex;flex-flow:column;justify-content: center;}
  nav{display:flex;
    flex-flow:row;
    justify-content:center;
    height:auto;
    margin:auto;}
button{margin:1rem;}
header{
  z-index:5;
  position:relative;
  display:flex;
  flex-flow:row;
  justify-content: space-between;
  padding: 2rem;
  height: 100px;
}
@media only screen and (max-width: 900px) {
  .main-title{
  margin-top:unset;}
  header{flex-flow:wrap;}
  .right-box{margin:auto;}
  .left-box{margin:auto;}
  header{height:auto;}
  .footer-text{font-size:0.6rem;}
}
footer{
  position:absolute;
  display:flex;
  flex-flow:row;
  justify-content:center;
  bottom:0px;
  left:0px;
  width:calc(100vw - 4rem);
  height:50px;
  padding-right:2rem;padding-left:2rem;}


</style>
