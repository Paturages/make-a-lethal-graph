<script>
  export let deadCash;
  export let cash;
  export let top;
  let height;
  let deadHeight;

  $: {
    height = 100 * cash / top;
    deadHeight = 100 * deadCash / top;
  }
</script>

<div class="cash">
  <div class="dead-bar" style={`height: ${deadHeight}%`}></div>
  <div class="bar" style={`height: ${height}%`}></div>
  <div class="dead-value">▮{deadCash}</div>
  <div class="value">▮{cash}</div>
</div>

<style>
  .cash {
    margin-top: 50px;
    position: relative;
    height: 300px;
    width: 150px;

    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
  }
  
  .dead-bar {
    z-index: 1;
    background: #888;
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
  }

  .bar {
    z-index: 2;
    background: #fff;
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
  }

  .value, .dead-value {
    z-index: 3;
    font-weight: 900;
    font-size: 2.5rem;

    text-shadow: -2px -2px 0 #fff, 2px -2px 0 #fff, -2px 2px 0 #fff, 2px 2px 0 #fff;
    color: #f7577d;
  }

  .dead-value {
    color: #f757ad;
    font-size: 1.75rem;
    opacity: .7;
  }
</style>