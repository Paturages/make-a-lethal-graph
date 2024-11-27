<script>
  export let player;
  import TwitchLogo from '../assets/TwitchLogo.svelte';
  import YoutubeLogo from '../assets/YoutubeLogo.svelte';
</script>

<div class="player">
  <div class="picture">
    <img src={player.img} alt="" />
  </div>
  <div class="container">
    <div class="name">{player.name}</div>
    <div class="link">
      {#if player.platform === 'twitch'}
        <TwitchLogo />
        <span>{player.link}</span>
      {/if}
      {#if player.platform === 'youtube'}
        <YoutubeLogo />
        <span>&nbsp;{player.link}</span>
      {/if}
    </div>
  </div>
</div>

<style>
  .player {
    position: relative;
    height: 100px;
    width: 330px;
    margin-bottom: 10px;
  }

  .picture {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    overflow: hidden;

    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
  }

  .picture img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .container {
    background: #fff;
    position: absolute;
    bottom: 0;
    left: 10px;
    padding: 10px 10px 10px 110px;
    border-radius: 75px;
    width: 200px;
  }

  .name {
    color: #f7577d;
    font-weight: 900;
    font-size: 1.25rem;
  }

  .link {
    color: #f7577d;
    display: flex;
    align-items: center;
  }
</style>
