(() => {
  'use strict';
  const cv = document.getElementById('game'); const ctx = cv.getContext('2d');
  const W = cv.width, H = cv.height;
  const dpr = Math.max(1, Math.min(3, window.devicePixelRatio || 1));
  cv.width = W * dpr; cv.height = H * dpr; ctx.scale(dpr, dpr);
  const triesEl = document.getElementById('tries');
  const overlay = document.getElementById('overlay'), ovTitle = document.getElementById('ov-title'), ovSub = document.getElementById('ov-sub');
  let target, guessStr, tries, over, log;

  function reset() { target = 1 + Math.floor(Math.random() * 100); guessStr = ''; tries = 0; over = false; log = []; triesEl.textContent = '0'; overlay.classList.add('hidden'); }
  function submit() {
    if (over || guessStr === '') return;
    const n = +guessStr; tries++; triesEl.textContent = tries;
    if (n === target) { over = true; ovTitle.textContent = '猜中了！'; ovSub.textContent = '答案是 ' + target + '，用了 ' + tries + ' 次'; overlay.classList.remove('hidden'); }
    else log.push(n + (n < target ? ' 偏小 ↑' : ' 偏大 ↓'));
    if (log.length > 4) log.shift();
    guessStr = '';
  }
  function draw() {
    ctx.fillStyle = '#1a1c3a'; ctx.fillRect(0, 0, W, H);
    ctx.fillStyle = '#eef0ff'; ctx.textAlign = 'center'; ctx.textBaseline = 'middle';
    ctx.font = '16px sans-serif'; ctx.fillText('我想了一个 1-100 的数，猜猜看', W / 2, 40);
    ctx.font = 'bold 48px monospace'; ctx.fillStyle = '#ffd23f'; ctx.fillText(guessStr || '_', W / 2, 110);
    ctx.font = '14px sans-serif'; ctx.fillStyle = 'rgba(255,255,255,0.6)';
    ctx.fillText('用数字键输入，回车提交，退格删除', W / 2, 160);
    ctx.textAlign = 'left'; ctx.font = '15px monospace';
    for (let i = 0; i < log.length; i++) ctx.fillText('· ' + log[i], 40, 210 + i * 24);
    if (over) { ctx.textAlign = 'center'; ctx.fillStyle = '#43d97a'; ctx.font = 'bold 22px sans-serif'; ctx.fillText('🎉 猜中！', W / 2, H - 30); }
  }
  window.addEventListener('keydown', e => {
    if (e.key >= '0' && e.key <= '9') { if (guessStr.length < 3) guessStr += e.key; }
    else if (e.key === 'Backspace') guessStr = guessStr.slice(0, -1);
    else if (e.key === 'Enter') submit();
  });
  document.getElementById('new').addEventListener('click', reset);
  document.getElementById('ov-btn').addEventListener('click', reset);
  function loop() { draw(); requestAnimationFrame(loop); }
  reset(); requestAnimationFrame(loop);
})();
