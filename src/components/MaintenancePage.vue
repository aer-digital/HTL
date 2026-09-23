<template>
  <main class="maintenance-page" aria-labelledby="maintenance-title">
    <section class="maintenance-panel">
      <img class="brand-mark" src="../assets/images/logo_less.png" alt="HTL" />

      <p class="status-label">Site em atualização</p>
      <h1 id="maintenance-title">Estamos preparando uma nova experiência.</h1>
      <p class="message">
        A página da HTL está temporariamente fora do ar para receber informações
        mais completas sobre nossas soluções, projetos e serviços.
      </p>

      <div class="contact-strip" aria-label="Canais de contato da HTL">
        <a href="mailto:comercial@htlbrasil.com">comercial@htlbrasil.com</a>
        <span aria-hidden="true"></span>
        <a href="https://wa.me/5513988158703" target="_blank" rel="noopener">
          WhatsApp
        </a>
      </div>
    </section>
  </main>
</template>

<style scoped>
:global(*) {
  box-sizing: border-box;
}

:global(html) {
  min-height: 100%;
  background: #071018;
}

:global(body) {
  min-height: 100%;
  margin: 0;
  color: #f6f8f8;
  font-family:
    Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
    sans-serif;
}

:global(a) {
  color: inherit;
}

.maintenance-page {
  position: relative;
  display: grid;
  min-height: 100vh;
  min-height: 100dvh;
  place-items: center;
  overflow: hidden;
  padding: clamp(1.5rem, 4vw, 4.5rem);
  background:
    linear-gradient(105deg, rgba(7, 16, 24, 0.97) 0%, rgba(7, 16, 24, 0.86) 48%, rgba(7, 16, 24, 0.62) 100%),
    url("../assets/images/lamp_wide.png") center / cover no-repeat;
}

.maintenance-page::before {
  position: absolute;
  inset: 0;
  content: "";
  background:
    linear-gradient(rgba(255, 255, 255, 0.035) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.035) 1px, transparent 1px);
  background-size: 56px 56px;
  mask-image: linear-gradient(90deg, #000 0%, transparent 72%);
  pointer-events: none;
}

.maintenance-panel {
  position: relative;
  width: min(100%, 760px);
  margin-right: auto;
}

.brand-mark {
  width: clamp(88px, 13vw, 132px);
  height: auto;
  margin-bottom: clamp(3rem, 9vw, 6.25rem);
}

.status-label {
  width: fit-content;
  margin: 0 0 1.1rem;
  padding: 0.55rem 0.75rem;
  border: 1px solid rgba(155, 212, 220, 0.42);
  border-radius: 4px;
  color: #9bd4dc;
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.16em;
  line-height: 1;
  text-transform: uppercase;
}

h1 {
  max-width: 12ch;
  margin: 0;
  color: #ffffff;
  font-size: clamp(3rem, 9vw, 6.7rem);
  font-weight: 750;
  letter-spacing: 0;
  line-height: 0.94;
}

.message {
  max-width: 640px;
  margin: clamp(1.35rem, 3vw, 2rem) 0 0;
  color: rgba(246, 248, 248, 0.78);
  font-size: clamp(1rem, 2.15vw, 1.35rem);
  line-height: 1.58;
}

.contact-strip {
  display: flex;
  width: fit-content;
  max-width: 100%;
  flex-wrap: wrap;
  align-items: center;
  gap: 0.85rem;
  margin-top: clamp(2rem, 4vw, 3rem);
  color: #ffffff;
  font-size: 0.95rem;
  font-weight: 700;
}

.contact-strip a {
  border-bottom: 1px solid rgba(155, 212, 220, 0.58);
  outline-offset: 0.3rem;
  text-decoration: none;
  transition:
    border-color 180ms ease,
    color 180ms ease;
}

.contact-strip a:hover {
  border-color: #f2c94c;
  color: #f2c94c;
}

.contact-strip a:focus-visible {
  outline: 3px solid #f2c94c;
}

.contact-strip span {
  width: 6px;
  height: 6px;
  border-radius: 999px;
  background: #f2c94c;
}

@media (max-width: 640px) {
  .maintenance-page {
    align-items: end;
    padding: 1.25rem;
    background-position: 60% center;
  }

  .maintenance-panel {
    padding-bottom: 1rem;
  }

  .brand-mark {
    margin-bottom: 4rem;
  }

  h1 {
    max-width: 9ch;
  }

  .contact-strip {
    align-items: flex-start;
    flex-direction: column;
  }

  .contact-strip span {
    display: none;
  }
}
</style>
