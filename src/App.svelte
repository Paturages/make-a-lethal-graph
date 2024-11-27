<script>
  import Player from "./components/Player.svelte";
  import Cash from "./components/Cash.svelte";
  import { teamA, teamB, teamC, teamD } from "./assets/players";

  const copyPasteSheetHere = `0	0	642		0	0	1203		726	726	0		0	0	854`;

	const [
		teamACurrent,
		teamADead,
		teamAEndOfRound,,
		teamBCurrent,
		teamBDead,
		teamBEndOfRound,,
		teamCCurrent,
		teamCDead,
		teamCEndOfRound,,
		teamDCurrent,
		teamDDead,
		teamDEndOfRound,,
	] = copyPasteSheetHere.split('\t');

  let cash = [+teamAEndOfRound+(+teamACurrent), +teamBEndOfRound+(+teamBCurrent), +teamCEndOfRound+(+teamCCurrent), +teamDEndOfRound+(+teamDCurrent)];
  let deadCash = [+teamAEndOfRound+(+teamADead), +teamBEndOfRound+(+teamBDead), +teamCEndOfRound+(+teamCDead), +teamDEndOfRound+(+teamDDead)].map(x => Number(x));
  let topCash = 0;

  $: {
    topCash = Math.max(...cash, ...deadCash);
  }
</script>

<div class="bg"></div>
<main>
  <div class="team">
    <div class="team-name">Team A</div>
    {#each teamA as player}
      <Player {player} />
    {/each}
    <Cash deadCash={deadCash[0]} cash={cash[0]} top={topCash} />
  </div>

  <div class="team">
    <div class="team-name">Team B</div>
    {#each teamB as player}
      <Player {player} />
    {/each}
    <Cash deadCash={deadCash[1]} cash={cash[1]} top={topCash} />
  </div>

  <div class="team">
    <div class="team-name">Team C</div>
    {#each teamC as player}
      <Player {player} />
    {/each}
    <Cash deadCash={deadCash[2]} cash={cash[2]} top={topCash} />
  </div>

  <div class="team">
    <div class="team-name">Team D</div>
    {#each teamD as player}
      <Player {player} />
    {/each}
    <Cash deadCash={deadCash[3]} cash={cash[3]} top={topCash} />
  </div>
</main>

<style>
  .bg {
    background-image: url("./assets/bg.png");
    background-size: 120%;
    background-position: center;
    background-repeat: no-repeat;
    z-index: -1;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
  main {
    width: 100%;
    height: 100vh;

    display: flex;
    align-items: center;
    justify-content: center;
  }

  .team {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: 0 20px;
  }

  .team-name {
    font-size: 2.5rem;
    font-weight: 900;
    margin-bottom: 10px;
    
    text-shadow: -2px -2px 0 #fff, 2px -2px 0 #fff, -2px 2px 0 #fff, 2px 2px 0 #fff;
    color: #f7577d;
  }
</style>
