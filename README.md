<!--
Neon Terminal Profile README — Alex Popov
Palette:
  bg-deep: #060907
  neon:     #6CFFB1
  neon2:    #3BFF8A
  text:     #CFECDD
  dim:      #7DAF96
Typeface suggestion (client-side): SF Mono, JetBrains Mono, Menlo, Consolas, monospace
-->

<!-- FULL WIDTH HERO (SVG, animated grid + glow + blinking cursor) -->
<p align="center">
  <svg width="100%" viewBox="0 0 1200 340" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Alex Popov — Software Engineer">
    <defs>
      <!-- Background -->
      <linearGradient id="bg" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0%"  stop-color="#050806"/>
        <stop offset="100%" stop-color="#060907"/>
      </linearGradient>

      <!-- Neon Grid -->
      <pattern id="grid" width="40" height="40" patternUnits="userSpaceOnUse">
        <path d="M 40 0 L 0 0 0 40" fill="none" stroke="#1a2c25" stroke-width="1"/>
      </pattern>

      <!-- Soft vignette -->
      <radialGradient id="vignette" cx="50%" cy="55%" r="65%">
        <stop offset="0%" stop-color="#00000000"/>
        <stop offset="100%" stop-color="#000000AA"/>
      </radialGradient>

      <!-- Neon glow filter -->
      <filter id="glow" x="-50%" y="-50%" width="200%" height="200%">
        <feGaussianBlur stdDeviation="3" result="colored"/>
        <feMerge>
          <feMergeNode in="colored"/>
          <feMergeNode in="SourceGraphic"/>
        </feMerge>
      </filter>

      <!-- Scanline overlay -->
      <pattern id="scan" width="4" height="4" patternUnits="userSpaceOnUse">
        <rect width="4" height="2" fill="#00000022"/>
        <rect y="2" width="4" height="2" fill="#00000000"/>
      </pattern>

      <!-- Typing mask: animate rect width to reveal text -->
      <clipPath id="typingMask">
        <rect id="maskRect" x="210" y="120" width="0" height="60" rx="2" ry="2">
          <animate attributeName="width" values="0;720;720" dur="2.8s" begin="0.2s" fill="freeze" keyTimes="0;0.85;1" calcMode="spline" keySplines="0.2 0.6 0.2 1;0 0 1 1"/>
        </rect>
      </clipPath>
    </defs>

    <!-- Base background -->
    <rect width="1200" height="340" fill="url(#bg)"/>
    <!-- Grid -->
    <rect width="1200" height="340" fill="url(#grid)"/>
    <!-- Animated parallax glow lines -->
    <g opacity="0.25" filter="url(#glow)">
      <rect x="-1200" y="40" width="2400" height="1.2" fill="#6CFFB1">
        <animate attributeName="x" values="-1200;0;-1200" dur="14s" repeatCount="indefinite"/>
      </rect>
      <rect x="0" y="300" width="2400" height="1.2" fill="#3BFF8A">
        <animate attributeName="x" values="0;-1200;0" dur="18s" repeatCount="indefinite"/>
      </rect>
    </g>

    <!-- Vignette -->
    <rect width="1200" height="340" fill="url(#vignette)"/>

    <!-- Terminal header pill -->
    <g transform="translate(200,70)">
      <rect x="0" y="0" width="220" height="28" rx="6" fill="#0a1511" stroke="#173b2f" stroke-width="1"/>
      <circle cx="16" cy="14" r="4" fill="#213d33"/>
      <circle cx="30" cy="14" r="4" fill="#1a332a"/>
      <circle cx="44" cy="14" r="4" fill="#12251f"/>
      <text x="70" y="18" fill="#7DAF96" font-size="12" font-family="SFMono-Regular,Menlo,Consolas,monospace">/usr/bin/profile</text>
    </g>

    <!-- Name (with typing reveal and blinking cursor) -->
    <g font-family="SFMono-Regular,Menlo,Consolas,monospace" font-weight="600">
      <!-- Neon outer glow text -->
      <text x="210" y="160" font-size="40" fill="#6CFFB1" opacity="0.18" filter="url(#glow)">Alex Popov — Software Engineer</text>
      <!-- Solid text clipped by typing mask -->
      <g clip-path="url(#typingMask)">
        <text x="210" y="160" font-size="40" fill="#CFECDD">Alex Popov — Software Engineer</text>
      </g>
      <!-- Blinking cursor -->
      <rect id="cursor" x="210" y="132" width="12" height="32" fill="#6CFFB1">
        <animate attributeName="x" values="210;930" dur="2.8s" begin="0.2s" fill="freeze" keyTimes="0;0.85;1" calcMode="spline" keySplines="0.2 0.6 0.2 1;0 0 1 1"/>
        <animate attributeName="opacity" values="1;0;1" dur="1.1s" repeatCount="indefinite"/>
      </rect>
    </g>

    <!-- Subtle scanlines -->
    <rect width="1200" height="340" fill="url(#scan)" opacity="0.12"/>
  </svg>
</p>

<!-- STACK: minimal info, rich UI -->
<p align="center">
  <img alt="" src="https://img.shields.io/badge/-STACK-060907?style=for-the-badge&labelColor=0b1511&color=0b1511&logo=terminal&logoColor=6CFFB1">
</p>

<div align="center">

<!-- Neon chip row -->
<table>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/LANG-TypeScript%20·%20Go%20·%20Python%20·%20C%2B%2B-060907?style=flat&labelColor=0a1511&color=0a1511&logoColor=6CFFB1">
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/FRONT-React%20·%20Next.js%20·%20Tailwind-060907?style=flat&labelColor=0a1511&color=0a1511&logoColor=6CFFB1">
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/BACK-Node.js%20·%20Fastify%20·%20tRPC%20·%20gRPC-060907?style=flat&labelColor=0a1511&color=0a1511&logoColor=6CFFB1">
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/DATA-Postgres%20·%20Redis%20·%20Prisma-060907?style=flat&labelColor=0a1511&color=0a1511&logoColor=6CFFB1">
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/OPS-Docker%20·%20AWS%20·%20Vercel%20·%20GitHub%20Actions-060907?style=flat&labelColor=0a1511&color=0a1511&logoColor=6CFFB1">
    </td>
  </tr>
</table>

</div>

<!-- Thin neon divider -->
<p align="center">
  <svg width="720" height="6" viewBox="0 0 720 6" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <linearGradient id="line" x1="0" y1="0" x2="1" y2="0">
        <stop offset="0" stop-color="#0d201a"/>
        <stop offset="0.5" stop-color="#6CFFB1"/>
        <stop offset="1" stop-color="#0d201a"/>
      </linearGradient>
      <filter id="soft" x="-50%" y="-50%" width="200%" height="200%">
        <feGaussianBlur stdDeviation="1.2"/>
      </filter>
    </defs>
    <rect x="0" y="2" width="720" height="2" fill="url(#line)" filter="url(#soft)" opacity="0.9"/>
  </svg>
</p>

<!-- Tiny credo (still minimal info) -->
<p align="center">
  <sub><i>typed edges • observability first • simplicity scales</i></sub>
</p>
