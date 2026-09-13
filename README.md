(() => {
  'use strict';
  const cv = document.getElementById('game'); const ctx = cv.getContext('2d');
  const W = cv.width, H = cv.height;
  const dpr = Math.max(1, Math.min(3, window.devicePixelRatio || 1));
  cv.width = W * dpr; cv.height = H * dpr; ctx.scale(dpr, dpr);
  const youEl = document.getElementById('you'), cpuEl = document.getElementById('cpu'), drawEl = document.getElementById('draw');
  const overlay = document.getElementById('overlay'), ovTitle = document.getElementById('ov-title'), ovSub = document.getElementById('ov-sub');
  const CH = ['✊', '✌️', '✋']; const NAMES = ['石头', '剪刀', '布'];
  const BW = (W - 80) / 3, BH = 90, BY = 200;
  let youC, cpuC, result;

  function reset() { youC = null; cpuC = null; result = ''; youEl.textContent = '0'; cpuEl.textContent = '0'; drawEl.textContent = '0'; overlay.classList.add('hidden'); }
  function play(i) {
    youC = i; cpuC = Math.floor(Math.random() * 3);
    const win = (youC === 0 && cpuC === 1) || (youC === 1 && cpuC === 2) || (youC === 2 && cpuC === 0);
    if (youC === cpuC) { drawEl.textContent = +drawEl.textContent + 1; result = '平局'; }
    else if (win) { youEl.textContent = +youEl.textContent + 1; result = '你赢了！'; }
    else { cpuEl.textContent = +cpuEl.textContent + 1; result = '电脑赢了'; }
  }
  function clickHandler(e) {
    const rect = cv.getBoundingClientRect(); const px = (e.clientX - rect.left) / rect.width * W, py = (e.clientY - rect.top) / rect.height * H;
    for (let i = 0; i < 3; i++) { const x = 20 + i * (BW + 20); if (px >= x && px <= x + BW && py >= BY && py <= BY + BH) play(i); }
  }
  function draw() {
    ctx.fillStyle = '#1a1c3a'; ctx.fillRect(0, 0, W, H);
    ctx.textAlign = 'center'; ctx.textBaseline = 'middle';
    ctx.font = '18px sans-serif'; ctx.fillStyle = '#eef0ff'; ctx.fillText('你出：' + (youC === null ? '？' : CH[youC]) + '   电脑：' + (cpuC === null ? '？' : CH[cpuC]), W / 2, 60);
    ctx.font = 'bold 24px sans-serif'; ctx.fillStyle = '#ffd23f'; ctx.fillText(result || '点击出拳', W / 2, 120);
    for (let i = 0; i < 3; i++) {
      const x = 20 + i * (BW + 20);
      ctx.fillStyle = '#34386e'; ctx.fillRect(x, BY, BW, BH);
      ctx.font = '40px serif'; ctx.fillStyle = '#fff'; ctx.fillText(CH[i], x + BW / 2, BY + BH / 2 - 10);
      ctx.font = '14px sans-serif'; ctx.fillText(NAMES[i], x + BW / 2, BY + BH - 14);
    }
  }
  cv.addEventListener('click', clickHandler);
  cv.addEventListener('touchend', e => { const t = e.changedTouches[0]; clickHandler({ clientX: t.clientX, clientY: t.clientY }); }, { passive: true });
  document.getElementById('new').addEventListener('click', reset);
  document.getElementById('ov-btn').addEventListener('click', reset);
  function loop() { draw(); requestAnimationFrame(loop); }
  reset(); requestAnimationFrame(loop);
})();
