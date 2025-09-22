<template>
   <div>
      <div class="container">
         <div class="banner" :class="{ 'banner-clicked': isBannerClicked }">
            <a :href="videoSrc" class="side one" @click.prevent="show">
               <img class="img" src="/assets/images/zhaga.png" />
            </a>
         </div>
      </div>
      <!-- Usamos teleport para adicionar o overlay e o iframe no body -->
      <teleport to="body">
         <div v-if="overlayVisible" class="overlay" @click="closeVideo"></div>
         <div id="main" v-if="overlayVisible">
            <div class="header">
               <h2>Eagle eye Zhaga</h2>
            </div>

            <div class="content">
               <div class="img">
                  <img src="/assets/images/zhaga.png" alt="">
               </div>
               <div class="datasheet">
                  <h3>Detalhes técnicos</h3>
                  <div class="grid">
                     <div>
                        <h3>Elétrica</h3>
                        <ul>
                           <li>24 VCC do driver de LED</li>
                           <li>III (SELV)</li>
                           <li>< 1 W</li>
                        </ul>
                     </div>

                     <div>
                        <h3>Comunicação</h3>
                        <ul>
                           <li>868,35 MHz / 915 MHz</li>
                           <li>≤16 dBm (39,81 mW)</li>
                           <li>≤16 dBm (39,81 mW)</li>
                        </ul>
                     </div>

                     <div>
                        <h3>Detecção</h3>
                        <ul>
                           <li>24.050 - 24.250 GHz</li>
                           <li>≤12 dBm (15,85 mW)</li>
                           <li>Radar Doppler (detector de movimento)</li>
                        </ul>
                     </div>

                     <div>
                        <h3>Mecânico</h3>
                        <ul>
                           <li>(-30 a +60 °C)</li>
                           <li>IP66</li>
                           <li>Luran (mistura de PC e ASA)</li>
                           <li>RAL7016 Cinza antracite</li>
                           <li>89 x 89 x 53 (milímetro)</li>
                           <li>125 g</li>
                        </ul>
                     </div>
                  </div>
               </div>
            </div>
         </div>
      </teleport>
   </div>
</template>

<script setup>
import { ref } from 'vue';

const isBannerClicked = ref(false); // Controla o estado do banner
const overlayVisible = ref(false); // Controla a visibilidade do overlay

// Função para reproduzir o vídeo
function show(event) {
   isBannerClicked.value = true;
   overlayVisible.value = true;

}

// Função para fechar o vídeo e limpar o estado
function closeVideo() {
   isBannerClicked.value = false;
   overlayVisible.value = false;
}
</script>

<style lang="scss" scoped>
.container {
   width: 230px;
   aspect-ratio: 2/3;
   position: relative;
   z-index: 2000;
}

.banner {
   width: 100%;
   height: 100%;
   -webkit-transform-style: preserve-3d;
   -webkit-transition: all 0.3s ease-in-out;
   -moz-transform-style: preserve-3d;
   -moz-transition: all 0.3s ease-in-out;
   -ms-transform-style: preserve-3d;
   -ms-transition: all 0.3s ease-in-out;
}

.container:hover .banner {
   -webkit-transform: rotateY(-15deg);
   -moz-transform: rotateY(-15deg);
   -ms-transform: rotateY(-15deg);
}

.banner-clicked {
   -webkit-transform: rotateY(-180deg) !important;
   -webkit-transition: all 0.7s cubic-bezier(0.67, 0.19, 0.31, 1.25) !important;
   -moz-transform: rotateY(-180deg) !important;
   -moz-transition: all 0.7s cubic-bezier(0.67, 0.19, 0.31, 1.25) !important;
   -ms-transform: rotateY(-180deg) !important;
   -ms-transition: all 0.7s cubic-bezier(0.67, 0.19, 0.31, 1.25) !important;
}

.side {
   position: absolute;
   -webkit-backface-visibility: hidden;
   -moz-backface-visibility: hidden;
   -ms-backface-visibility: hidden;
   padding: 4px;
   background: rgba(255, 255, 255, 0.2);
   border-radius: 16px;
   box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
   backdrop-filter: blur(5px);
   -webkit-backdrop-filter: blur(5px);
   border: 1px solid rgba(255, 255, 255, 0.3);
   z-index: 1000;
}

.one {
   display: block;
   width: 100%;
   height: 100%;
   -webkit-transform: rotateY(0deg);
   -moz-transform: rotateY(0deg);
   -ms-transform: rotateY(0deg);
   cursor: pointer;
   text-decoration: none;
   border: none;
}

.one:before {
   content: '';
   display: block;
   width: 48px;
   height: 48px;
   background: url(https://dl.dropbox.com/u/10873105/youtubePlay.png) 0 0 no-repeat;
   position: absolute;
   top: 50%;
   margin-top: -24px;
   left: 50%;
   margin-left: -24px;
   opacity: 0.8;
   zoom: 0.9;
   -webkit-transition: opacity 0.2s ease-in-out;
   -moz-transition: opacity 0.2s ease-in-out;
   -ms-transition: opacity 0.2s ease-in-out;
}

.one:hover:before {
   opacity: 0.9;
}

.overlay {
   position: fixed;
   /* Fixa o overlay cobrindo a tela inteira */
   top: 0;
   left: 0;
   width: 100%;
   height: 100%;
   background: rgba(0, 0, 0, 0.8);
   /* Fundo escuro com opacidade */
   z-index: 10000;
   cursor: pointer;
}

#main {
   position: fixed;
   display: flex;
   flex-direction: column;
   width: 60vw;
   height: 60vh;
   background: #eaeaea55;
   backdrop-filter: blur(5px);
   top: 50%;
   left: 50%;
   transform: translate(-50%, -50%);
   z-index: 10001;
   border-radius: 10px;
   box-shadow: 0 4px 30px rgba(0, 0, 0, 0.2);
   padding: 2rem;
   overflow-y: scroll;

   @media screen and (max-width: 768px) {
      width: 90vw;
      height: 70vh;

      .content{
         flex-direction: column-reverse;
      }
   }

   scrollbar-color: grey transparent;

   .header {

   }

   .content {
      display: flex;

      .img{
         flex: 1;
         margin-top: 2rem;

         img{
            width: 100%;
            object-fit: contain;
         }
      }
      .datasheet{
         flex: 2;

         .grid{
            display: grid;
            grid-template-columns: repeat(2, 1fr); /* 2 colunas do mesmo tamanho */
            grid-template-rows: auto; /* altura conforme o conteúdo */
            grid-column-gap: 10px;
            grid-row-gap: 10px;

            div{
               background: #eaeaea55;
               border-radius: .5rem;
               padding: 1.3rem;
            }
         }
      }
      
   }
}

img.img {
   width: 100%;
   height: 100%;
   object-fit: contain;
   //   padding: 20px;
}

</style>
