<script>
  import { onMount, onDestroy } from "svelte";

  const TRAIL = 14;
  const HEAD_SIZE = 12;
  const TAIL_MIN = 2.5;
  const FOLLOW = 0.28;
  const CHAIN = 0.32;

  let x = 0, y = 0;
  let dots = Array.from({ length: TRAIL }, () => ({ x: 0, y: 0 }));
  let raf;

  function handleMove(e) {
    x = e.clientX;
    y = e.clientY;
  }

  function loop() {
    dots[0].x += (x - dots[0].x) * FOLLOW;
    dots[0].y += (y - dots[0].y) * FOLLOW;
    for (let i = 1; i < dots.length; i++) {
      dots[i].x += (dots[i - 1].x - dots[i].x) * CHAIN;
      dots[i].y += (dots[i - 1].y - dots[i].y) * CHAIN;
    }
    raf = requestAnimationFrame(loop);
  }

  onMount(() => {
    document.documentElement.classList.add("hide-default-cursor");
    window.addEventListener("mousemove", handleMove);
    raf = requestAnimationFrame(loop);

    return () => {
      document.documentElement.classList.remove("hide-default-cursor");
      window.removeEventListener("mousemove", handleMove);
      cancelAnimationFrame(raf);
    };
  });
</script>

<style>
  /* This hides the browser pointer everywhere */
  :global(.hide-default-cursor),
  :global(.hide-default-cursor *) {
    cursor: none !important;
  }

  .cursor {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 2147483647;
    mix-blend-mode: screen;
  }

  .dot {
    position: absolute;
    left: 0;
    top: 0;
    transform: translate(calc(var(--x) * 1px), calc(var(--y) * 1px)) translate(-50%, -50%);
    width: calc(var(--s) * 1px);
    height: calc(var(--s) * 1px);
    border-radius: 999px;
    opacity: var(--o);
    background: radial-gradient(circle, rgba(0, 210, 255, 1) 0%, rgba(0, 110, 255, 0.8) 60%, rgba(0, 60, 255, 0.4) 100%);
    box-shadow:
      0 0 8px rgba(0, 210, 255, 1),
      0 0 16px rgba(0, 180, 255, 0.9),
      0 0 32px rgba(0, 150, 255, 0.8);
    animation: breathe 1.9s ease-in-out infinite;
  }

  @keyframes breathe {
    0%, 100% { transform: translate(calc(var(--x) * 1px), calc(var(--y) * 1px)) translate(-50%, -50%) scale(0.9); }
    50% { transform: translate(calc(var(--x) * 1px), calc(var(--y) * 1px)) translate(-50%, -50%) scale(1.15); }
  }
</style>

<div class="cursor">
  {#each dots as d, i}
    <div
      class="dot"
      style="
        --x:{d.x};
        --y:{d.y};
        --s:{i === 0 ? HEAD_SIZE : Math.max(HEAD_SIZE - i * ((HEAD_SIZE - TAIL_MIN) / (TRAIL - 1)), TAIL_MIN)};
        --o:{Math.max(1 - i * (0.85 / (TRAIL - 1)), 0.15)};
      "
    />
  {/each}
</div>
