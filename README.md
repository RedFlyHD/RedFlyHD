<style>
  @import url("https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,500&display=swap");

:root {
  --shiny-cta-bg: #000000;
  --shiny-cta-bg-subtle: #1a1818;
  --shiny-cta-fg: #ffffff;
  --shiny-cta-highlight: #ff4c04;
  --shiny-cta-highlight-subtle: #ffa1a1;
}

@property --gradient-angle {
  syntax: "<angle>";
  initial-value: 0deg;
  inherits: false;
}

@property --gradient-angle-offset {
  syntax: "<angle>";
  initial-value: 0deg;
  inherits: false;
}

@property --gradient-percent {
  syntax: "<percentage>";
  initial-value: 5%;
  inherits: false;
}

@property --gradient-shine {
  syntax: "<color>";
  initial-value: white;
  inherits: false;
}

.shiny-cta {
  --animation: gradient-angle linear infinite;
  --duration: 3s;
  --shadow-size: 2px;
  isolation: isolate;
  position: relative;
  overflow: hidden;
  cursor: pointer;
  outline-offset: 4px;
  padding: 1.25rem 2.5rem;
  font-family: inherit;
  font-size: 1.125rem;
  line-height: 1.2;
  border: 1px solid transparent;
  border-radius: 0px;
  color: var(--shiny-cta-fg);
  background: linear-gradient(var(--shiny-cta-bg), var(--shiny-cta-bg))
      padding-box,
    conic-gradient(
        from calc(var(--gradient-angle) - var(--gradient-angle-offset)),
        transparent,
        var(--shiny-cta-highlight) var(--gradient-percent),
        var(--gradient-shine) calc(var(--gradient-percent) * 2),
        var(--shiny-cta-highlight) calc(var(--gradient-percent) * 3),
        transparent calc(var(--gradient-percent) * 4)
      )
      border-box;
  box-shadow: inset 0 0 0 1px var(--shiny-cta-bg-subtle);

  &::before,
  &::after,
  span::before {
    content: "";
    pointer-events: none;
    position: absolute;
    inset-inline-start: 50%;
    inset-block-start: 50%;
    translate: -50% -50%;
    z-index: -1;
  }
s
}

/* Dots pattern */
.shiny-cta::before {
  --size: calc(100% - var(--shadow-size) * 3);
  --position: 2px;
  --space: calc(var(--position) * 2);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(
      circle at var(--position) var(--position),
      white calc(var(--position) / 4),
      transparent 0
    )
    padding-box;
  background-size: var(--space) var(--space);
  background-repeat: space;
  -webkit-mask-image: conic-gradient(
    from calc(var(--gradient-angle) + 45deg),
    black,
    transparent 10% 90%,
    black
  );
          mask-image: conic-gradient(
    from calc(var(--gradient-angle) + 45deg),
    black,
    transparent 10% 90%,
    black
  );
  border-radius: inherit;
  opacity: 0.4;
  z-index: -1;
}

/* Inner shimmer */
.shiny-cta::after {
  --animation: shimmer linear infinite;
  width: 100%;
  aspect-ratio: 1;
  background: linear-gradient(
    -50deg,
    transparent,
    var(--shiny-cta-highlight),
    transparent
  );
  -webkit-mask-image: radial-gradient(circle at bottom, transparent 40%, black);
          mask-image: radial-gradient(circle at bottom, transparent 40%, black);
  opacity: 0.6;
}

.shiny-cta span {
  z-index: 1;

  &::before {
    --size: calc(100% + 1rem);
    width: var(--size);
    height: var(--size);
    box-shadow: inset 0 -1ex 2rem 4px var(--shiny-cta-highlight);
    opacity: 0;
  }
}

/* Animate */
.shiny-cta {
  --transition: 800ms cubic-bezier(0.25, 1, 0.5, 1);
  transition: var(--transition);
  transition-property: --gradient-angle-offset, --gradient-percent,
    --gradient-shine;

  &,
  &::before,
  &::after {
    animation: var(--animation) var(--duration),
      var(--animation) calc(var(--duration) / 0.4) reverse paused;
    animation-composition: add;
  }

  span::before {
    transition: opacity var(--transition);
    -webkit-animation: calc(var(--duration) * 1.5) breathe linear infinite;
            animation: calc(var(--duration) * 1.5) breathe linear infinite;
  }
}

.shiny-cta:is(:hover, :focus-visible) {
  --gradient-percent: 20%;
  --gradient-angle-offset: 95deg;
  --gradient-shine: var(--shiny-cta-highlight-subtle);

  &,
  &::before,
  &::after {
    -webkit-animation-play-state: running;
            animation-play-state: running;
  }

  span::before {
    opacity: 1;
  }
}

@-webkit-keyframes gradient-angle {
  to {
    --gradient-angle: 360deg;
  }
}

@keyframes gradient-angle {
  to {
    --gradient-angle: 360deg;
  }
}

@-webkit-keyframes shimmer {
  to {
    rotate: 360deg;
  }
}

@keyframes shimmer {
  to {
    rotate: 360deg;
  }
}

@-webkit-keyframes breathe {
  from,
  to {
    scale: 1;
  }
  50% {
    scale: 1.2;
  }
}

@keyframes breathe {
  from,
  to {
    scale: 1;
  }
  50% {
    scale: 1.2;
  }
}

html,
body {
  height: 100%;
}

body {
  display: grid;
  place-items: center;
  color: white;
  background: #02040c;
  font-family: "Inter", sans-serif;
  font-optical-sizing: auto;
  font-weight: 500;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
}
</style>
<body>
<!-- partial:index.partial.html -->
 <a href="https://doReNew.tech">
  <button class="shiny-cta">
    <span>Change the world together.</span>
  </button>
 </a>
<!-- partial -->
  
</body>
