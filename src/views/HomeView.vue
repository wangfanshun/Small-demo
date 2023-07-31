<template>
  <div class="home">
    <ul class='grid-ul' id='ul-el'>
      <li><img index=0 src="../assets/logo.png" alt=""></li>
      <li><img index=1 src="../assets/logo.png" alt=""></li>
      <li><img index=2 src="../assets/logo.png" alt=""></li>
      <li><img index=3 src="../assets/logo.png" alt=""></li>
      <li><img index=4 src="../assets/logo.png" alt=""></li>
      <li><img index=5 src="../assets/logo.png" alt=""></li>
      <li><img index=6 src="../assets/logo.png" alt=""></li>
      <li><img index=7 src="../assets/logo.png" alt=""></li>
      <li><img index=8 src="../assets/logo.png" alt=""></li>
      <div class="mask" id='mask'></div>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'pngselect',
  mounted(){
    const ulEl=document.getElementById('ul-el')
    ulEl.addEventListener('mouseover', (e)=>{
      const target=e.target
      if(target.tagName=='IMG'){
        const maskEl=document.getElementById('mask')
        const index=target.getAttribute('index')
        const row=Math.floor(Number(index)/3)
        const column=Number(index)%3
        maskEl.style.setProperty('--row',row)
        maskEl.style.setProperty('--column',column)
      }
    })
  }
}
</script>
<style scoped lang='scss'>
.grid-ul{
  --gap:10px;
  --w:200px;
  --h:200px;
  --distance:calc(var(--w) + var(--gap));
  position: relative;
  display: grid;
  grid-template-columns: repeat(3,var(--w));
  grid-template-rows: repeat(3,var(--h));
  grid-gap: var(--gap) var(--gap);
  padding: var(--gap);
  width: fit-content;
  .mask{
    --row:0;
    --column:0;
    position: absolute;
    top: calc(var(--gap) / 2);
    left: calc(var(--gap) / 2);
    width: calc(var(--w) + var(--gap));
    height: calc(var(--h) + var(--gap));
    border:1px solid red;
    opacity: 1; /* 初始时设置完全不透明 */
    transform:translate(calc(var(--distance) * var(--column)),calc(var(--distance) * var(--row)));
    transition: transform 0.2s ease;
    // --webkit-mask: conic-gradient(at 50px 50px, transparent 75%,blue 75% 100%) 0 0 / calc(100% - 50px) calc(100% - 50px) 
  }
}
</style>

