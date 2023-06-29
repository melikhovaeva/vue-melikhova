<template>
  <section class="add-comment">
    <div class="add-comment__wrapper">
      <h2 class="add-comment__title">Создание комментария</h2>
      <form class="add-comment__form" @submit.prevent="createComment">
        <label class="add-comment__label">
          Автор: 
          <my-input 
            v-model.trim="formData.author" 
            name="author" 
            type="text" 
            placeholder="Enter your name..." 
            required>
          </my-input>
        </label>
        <label class="add-comment__label">
          Комментарий: 
          <my-input
            v-model.trim="formData.text" 
            name="comment"
            type="text" 
            placeholder="Enter your text..." 
            required>
          </my-input>
        </label>
        <label class="add-comment__label add-comment__label--radio">
          <input
            v-model="formData.reaction"
            type="radio"
            name="reaction"
            value="1"
            required
            />
          <svg class="add-comment__icon" viewBox="0 0 519 519">
            <defs>
              <radialGradient cx="50%" cy="18.3997132%" fx="50%" fy="18.3997132%" id="radialGradient-1" r="59.6759141%">
                <stop offset="0%" stop-color="#FDE990"/><stop offset="100%" stop-color="#FACE57"/>
              </radialGradient>
              <radialGradient cx="50%" cy="44.7705207%" fx="50%" fy="44.7705207%" gradientTransform="translate(0.500000,0.447705),rotate(-88.879799),scale(1.000000,1.022987),translate(-0.500000,-0.447705)" id="radialGradient-2" r="49.9681774%">
                <stop offset="0%" stop-color="#D27C12" stop-opacity="0.186216128"/>
                <stop offset="85.6313345%" stop-color="#D27C12" stop-opacity="0"/>
                <stop offset="100%" stop-color="#D27C12" stop-opacity="0.324546547"/>
              </radialGradient><linearGradient id="linearGradient-3" x1="50%" x2="50%" y1="0%" y2="100%">
                <stop offset="0%" stop-color="#000000"/><stop offset="100%" stop-color="#887133"/>
              </linearGradient><linearGradient id="linearGradient-4" x1="50%" x2="50%" y1="0%" y2="100%">
                <stop offset="0%" stop-color="#E95050"/><stop offset="99.1026182%" stop-color="#E85B5B"/>
              </linearGradient>
              <path d="M165.074118,81.4038462 C215.579865,81.4038462 262.213145,87.3079835 299.827999,97.2837828 
              C269.661678,138.784226 220.667659,165.771978 165.354995,165.771978 C109.98689,165.771978 60.9501021,138.730097 
              30.7922131,97.1635028 C68.3250841,87.2587191 114.779523,81.4038462 165.074118,81.4038462 Z" id="path-5"/>
              <filter filterUnits="objectBoundingBox" height="126.1%" id="filter-6" width="108.2%" x="-4.1%" y="-13.0%">
                <feGaussianBlur in="SourceAlpha" result="shadowBlurInner1" stdDeviation="10.5"/>
                <feOffset dx="0" dy="1" in="shadowBlurInner1" result="shadowOffsetInner1"/>
                <feComposite in="shadowOffsetInner1" in2="SourceAlpha" k2="-1" k3="1" operator="arithmetic" result="shadowInnerInner1"/>
                <feColorMatrix in="shadowInnerInner1" type="matrix" values="0 0 0 0 0   0 0 0 0 0   0 0 0 0 0  0 0 0 0.5 0"/>
              </filter>
              <filter filterUnits="objectBoundingBox" height="239.5%" id="filter-7" width="148.0%" x="-24.0%" y="-69.8%">
                <feGaussianBlur in="SourceGraphic" stdDeviation="10"/></filter></defs><g fill="none" fill-rule="evenodd" id="Page-1" stroke="none" stroke-width="1">
                  <g id="Artboard" transform="translate(-2412.000000, -821.000000)">
                    <g id="Group-7" transform="translate(2412.000000, 821.000000)">
                      <circle cx="259.5" cy="259.5" fill="url(#radialGradient-1)" id="Oval" r="259.5"/>
                      <circle cx="259.5" cy="259.5" fill="url(#radialGradient-2)" id="Oval" r="259.5"/><g id="Group-3" transform="translate(95.000000, 310.000000)">
                        <path d="M159.857362,0.228021978 C212.600491,0.228021978 269.580872,5.28076883 330.798506,15.3862625 C323.127384,99.7099504 
                        252.038239,165.771978 165.475496,165.771978 C79.3292942,165.771978 8.50813082,100.344203 0.261661067,16.6039967 
                        C51.8391959,5.68654764 105.037265,0.228021978 159.857362,0.228021978 Z" fill="url(#linearGradient-3)" id="Oval-3" opacity="0.879673549"/>
                        <g id="Oval-4"><use fill="url(#linearGradient-4)" fill-rule="evenodd" xlink:href="#path-5"/>
                        <use fill="black" fill-opacity="1" filter="url(#filter-6)" xlink:href="#path-5"/>
                        </g>
                    </g>
                    <ellipse cx="260.5" cy="422.5" fill="#FF8989" filter="url(#filter-7)" id="Oval" opacity="0.397251674" rx="62.5" ry="21.5"/>
                    <path d="M81.4404415,231.695202 C83.1883636,225.435935 89.6388608,221.750844 95.9107321,223.388584 L96.1007291,223.439844 
                    L182.296016,247.444958 C193.82001,250.654354 193.888144,266.85635 182.575553,270.259917 L182.229263,270.359111 L96.9402415,293.578577 
                    C90.5990005,295.304944 84.0570115,291.570819 82.3283001,285.238175 C80.6168759,278.968857 84.2645457,272.503052 90.4905701,270.69927 
                    L90.6800238,270.646042 L134.329328,258.76274 L89.707006,246.335616 C83.4392414,244.590063 79.749148,238.148311 81.3891114,231.884942 
                    L81.4404415,231.695202 Z" fill="#251C0C" fill-rule="nonzero" id="Path-5"/><path d="M328.440442,231.695202 C330.188364,225.435935 
                    336.638861,221.750844 342.910732,223.388584 L343.100729,223.439844 L429.296016,247.444958 C440.82001,250.654354 440.888144,266.85635 
                    429.575553,270.259917 L429.229263,270.359111 L343.940242,293.578577 C337.599001,295.304944 331.057012,291.570819 329.3283,285.238175 
                    C327.616876,278.968857 331.264546,272.503052 337.49057,270.69927 L337.680024,270.646042 L381.329328,258.76274 L336.707006,246.335616 
                    C330.439241,244.590063 326.749148,238.148311 328.389111,231.884942 L328.440442,231.695202 Z" fill="#251C0C" fill-rule="nonzero" id="Path-5" transform="translate(383.000000, 258.500000) scale(-1, 1) translate(-383.000000, -258.500000) "/>
                    </g>
                  </g>
              </g>
          </svg>
        </label>
        <label class="add-comment__label add-comment__label--radio">
          <input
            v-model="formData.reaction"
            type="radio"
            required
            name="reaction"
            value="0"
            checked
          />
          <svg class="add-comment__icon" viewBox="0 0 519 519">
            <defs>
            <radialGradient cx="50%" cy="18.3997132%" fx="50%" fy="18.3997132%" id="radialGradient-1" r="59.6759141%">
              <stop offset="0%" stop-color="#FDE990"/>
              <stop offset="100%" stop-color="#FACE57"/>
            </radialGradient>
            <radialGradient cx="50%" cy="46.4640335%" fx="50%" fy="46.4640335%" gradientTransform="translate(0.500000,0.464640),rotate(-90.000000),scale(1.000000,1.065220),translate(-0.500000,-0.464640)" id="radialGradient-2" r="56.1203663%">
              <stop offset="0%" stop-color="#D27C12" stop-opacity="0.186216128"/>
              <stop offset="82.3426943%" stop-color="#D27C12" stop-opacity="0"/>
              <stop offset="100%" stop-color="#D27C12" stop-opacity="0.176081731"/>
            </radialGradient>
            <radialGradient cx="50%" cy="50%" fx="50%" fy="50%" id="radialGradient-3" r="50%">
              <stop offset="0%" stop-color="#F6756A"/>
              <stop offset="100%" stop-color="#F66F6A" stop-opacity="0"/>
            </radialGradient>
            </defs>
            <g fill="none" fill-rule="evenodd" id="Page-1" stroke="none" stroke-width="1">
            <g id="Artboard" transform="translate(-3303.000000, -821.000000)">
            <g id="Group" transform="translate(3303.000000, 821.000000)">
            <circle cx="259.5" cy="259.5" fill="url(#radialGradient-1)" id="Oval" r="259.5"/>
            <circle cx="259.5" cy="259.5" fill="url(#radialGradient-2)" id="Oval" r="259.5"/>
            <path d="M128.558017,118 C160.301557,118 187.44679,140.590087 193.755509,171.601536 
            C195.070892,178.067492 190.947247,184.38614 184.54509,185.71463 C178.206956,187.029836 172.011774,182.961127 
            170.61219,176.605711 L170.571251,176.412425 C166.513664,156.466752 149.014922,141.904412 128.558017,141.904412 
            C104.868221,141.904412 85.6685446,161.276428 85.6685446,185.167163 C85.6685446,189.844694 86.4003432,194.406725 
            87.8185242,198.740596 L87.9626286,199.173218 C90.0796046,205.418386 86.7829979,212.214346 80.5994515,214.352418 
            C74.4159051,216.490491 67.6870022,213.161032 65.5700262,206.915864 C63.2153135,199.969363 62,192.643684 62,185.167163 
            C62,148.06914 91.8016339,118 128.558017,118 Z" fill="#251C0C" fill-rule="nonzero" id="Path"/>
            <path d="M318.558017,61 C350.301557,61 377.44679,83.5900869 383.755509,114.601536 C385.070892,121.067492 
            380.947247,127.38614 374.54509,128.71463 C368.206956,130.029836 362.011774,125.961127 360.61219,119.605711 
            L360.571251,119.412425 C356.513664,99.4667517 339.014922,84.9044116 318.558017,84.9044116 C294.868221,84.9044116 
            275.668545,104.276428 275.668545,128.167163 C275.668545,132.844694 276.400343,137.406725 277.818524,141.740596 
            L277.962629,142.173218 C280.079605,148.418386 276.782998,155.214346 270.599452,157.352418 C264.415905,159.490491 
            257.687002,156.161032 255.570026,149.915864 C253.215314,142.969363 252,135.643684 252,128.167163 C252,91.0691397 
            281.801634,61 318.558017,61 Z" fill="#251C0C" fill-rule="nonzero" id="Path"/><path d="M334.707059,215.748316 
            C338.092287,210.167275 345.449283,208.334626 351.13937,211.654978 C356.829456,214.975331 358.697914,222.191336 
            355.312686,227.772376 C330.222635,269.136973 292.767718,295.37636 247.254102,302.251223 C216.537318,306.891015 
            184.203578,302.282834 150.4189,288.61017 C144.298479,286.133235 141.384083,279.258785 143.909414,273.255657 
            C146.434746,267.25253 153.443513,264.393986 159.563934,266.870921 C189.476565,278.976567 217.43481,282.961156 
            243.604688,279.008177 C281.796587,273.239264 313.164682,251.264056 334.707059,215.748316 Z" fill="#251C0C" fill-rule="nonzero" id="Path-7"/>
            <circle cx="102" cy="263" fill="url(#radialGradient-3)" id="Oval" opacity="0.711053757" r="89"/>
            <circle cx="377" cy="178" fill="url(#radialGradient-3)" id="Oval" opacity="0.711053757" r="89"/>
            </g></g></g>
          </svg>
        </label>
        <label class="add-comment__label add-comment__label--radio">
          <input
            v-model="formData.reaction"
            type="radio"
            name="reaction"
            value="-1"
            required
        />
          <svg class="add-comment__icon" viewBox="0 0 519 519">
            <defs>
              <radialGradient cx="50%" cy="18.3997132%" fx="50%" fy="18.3997132%" gradientTransform="translate(0.500000,0.183997),scale(0.998077,1.000000),rotate(92.315592),translate(-0.500000,-0.183997)" id="radialGradient-1" r="59.6761013%">
                <stop offset="0%" stop-color="#FDE990"/><stop offset="100%" stop-color="#FACE57"/>
              </radialGradient><radialGradient cx="50%" cy="44.7705207%" fx="50%" fy="44.7705207%" gradientTransform="translate(0.500000,0.447705),scale(0.998077,1.000000),rotate(-88.877641),scale(1.000000,1.022987),translate(-0.500000,-0.447705)" id="radialGradient-2" r="49.9682142%">
                <stop offset="0%" stop-color="#D27C12" stop-opacity="0.186216128"/>
                <stop offset="85.6313345%" stop-color="#D27C12" stop-opacity="0"/>
                <stop offset="100%" stop-color="#D27C12" stop-opacity="0.324546547"/>
              </radialGradient>
              <linearGradient id="linearGradient-3" x1="54.0185272%" x2="45.9814728%" y1="0.372692418%" y2="99.6273076%">
                <stop offset="0%" stop-color="#251C0C"/>
                <stop offset="100%" stop-color="#000000"/>
              </linearGradient>
              <radialGradient cx="50%" cy="50%" fx="50%" fy="50%" gradientTransform="translate(0.500000,0.500000),scale(1.000000,0.540323),rotate(90.000000),translate(-0.500000,-0.500000)" id="radialGradient-4" r="92.5373134%">
                <stop offset="0%" stop-color="#71B5F8"/>
                <stop offset="100%" stop-color="#0073E4"/>
              </radialGradient>
            </defs>
            <g fill="none" fill-rule="evenodd" id="Page-1" stroke="none" stroke-width="1">
              <g id="Artboard" transform="translate(-1563.000000, -1625.000000)">
                <g id="Group-5" transform="translate(1563.000000, 1625.000000)">
                  <ellipse cx="259.500964" cy="259.001923" fill="url(#radialGradient-1)" id="Oval" rx="259.500964" ry="259.001923"/>
                  <ellipse cx="259.500963" cy="259.002885" fill="url(#radialGradient-2)" id="Oval" rx="259.500964" ry="259.001923"/>
                  <path d="M154.467082,245.347015 C170.159033,242.785728 186.227545,254.870171 188.682329,276.489932 C191.137114,298.109693 
                  179.048594,321.077808 163.356642,323.639095 C147.664691,326.200382 128.212307,315.025617 125.757523,293.405856 
                  C123.302739,271.786095 138.775131,247.908302 154.467082,245.347015 Z M157.209008,182 C163.786099,182 
                  169.117884,187.349264 169.117884,193.947915 C169.117884,200.546567 163.786099,205.895831 157.209008,205.895831 
                  C143.06815,205.895831 128.544211,211.849721 113.444929,224.22921 C108.352076,228.4047 100.84966,227.647497 
                  96.6878131,222.537949 C92.5259662,217.428401 93.2806952,209.90139 98.3735476,205.7259 C117.474112,190.065869 
                  137.15002,182 157.209008,182 Z" fill="url(#linearGradient-3)" id="Oval-2" opacity="0.879673549"/>
                  <path d="M395.467082,245.347015 C411.159033,242.785728 427.227545,254.870171 429.682329,276.489932 
                  C432.137114,298.109693 420.048594,321.077808 404.356642,323.639095 C388.664691,326.200382 369.212307,315.025617 
                  366.757523,293.405856 C364.302739,271.786095 379.775131,247.908302 395.467082,245.347015 Z M398.209008,182 
                  C404.786099,182 410.117884,187.349264 410.117884,193.947915 C410.117884,200.546567 404.786099,205.895831 
                  398.209008,205.895831 C384.06815,205.895831 369.544211,211.849721 354.444929,224.22921 C349.352076,228.4047 
                  341.84966,227.647497 337.687813,222.537949 C333.525966,217.428401 334.280695,209.90139 339.373548,205.7259 
                  C358.474112,190.065869 378.15002,182 398.209008,182 Z" fill="url(#linearGradient-3)" id="Oval-2" 
                  opacity="0.879673549" transform="translate(382.500000, 253.000000) scale(-1, 1) translate(-382.500000, -253.000000) "/>
                  <path d="M261.862067,370 C290.880425,370 317.30918,385.168257 332.211638,409.523562 C335.704214,415.23153 
                  333.924777,422.700172 328.237155,426.205241 C322.606408,429.675259 315.256176,427.959695 311.720892,422.386601 
                  L311.614936,422.21654 C301.064425,404.973687 282.391037,394.256468 261.862067,394.256468 C242.228371,394.256468 
                  224.272045,404.052984 213.490489,420.065781 L213.165977,420.552917 C209.483929,426.139665 201.986228,427.673053 
                  196.419392,423.977834 C190.852557,420.282615 189.324635,412.758094 193.006683,407.171345 C208.179588,384.149589 
                  233.831214,370 261.862067,370 Z" fill="#251C0C" fill-rule="nonzero" id="Path"/><path d="M109.5,506 C128.001539,506 
                  143,486.029967 143,461.395683 C143,444.972828 131.833333,418.5076 109.5,382 C87.1666667,418.5076 76,444.972828 
                  76,461.395683 C76,486.029967 90.9984609,506 109.5,506 Z" fill="url(#radialGradient-4)" id="Oval"/>
                </g>
              </g>
            </g>
          </svg>
        </label>
        <my-button
          class="add-comment__button">
          Создать
        </my-button>
      </form>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    parentCommentId:{
      type: Number,
      default: null  
    }
  },
  data() {
    return {
      formData: {
        author: '',
        text: '',
        reaction: 0,
        parentId: null,
      },
    }
  },
  methods: {
    createComment() {
      this.formData = {
        author: this.formData.author,
        text: this.formData.text,
        reaction: +this.formData.reaction,
        parentId: this.parentCommentId,
      };
      this.$emit('create', this.formData);
      this.formData = {
        author: '',
        text: '',
        reaction: 0,
        parentId: null,
      };
    },
  }
}
</script>

<style lang="scss" scoped>
.add-comment {
  margin: 20px;
  &__wrapper {
    max-width: 100%;
  }

  &__form {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  &__label {
    width: 100%;
    margin-top: 0.8rem;
    display: flex;
    flex-direction: column;
  }

  &__label--radio {
    flex-direction: row;
    align-items: center;
    margin-top: 1rem;
  }

  &__icon {
    margin-left: 0.5rem;
    max-width: 20px;
  }

  &__button {
    margin: 1rem auto;
  }
}
</style>