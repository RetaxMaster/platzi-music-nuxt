<template>

    <div class="container">
        <div class="columns">

            <div class="column is-3 has-text-centered">
                <figure class="media-left">
                    <p class="image">
                        <img :src="track.img">
                    </p>
                </figure>
            </div>

            <div class="column is-8">
                <div class="panel">
                    <div class="panel-heading">
                        <h1 class="title">{{ track.name }}</h1>
                    </div>
                    <div class="panel-block">
                        <article class="media">
                            <div class="media-content">

                                <div class="content">
                                    <!-- v-for también puede recorrer objetos, v representa cada propiedad de track, k reprenseta la key -->
                                    <ul v-for="(v, k) in track" :key="k">
                                        <li>
                                            <strong>{{ k }}:&nbsp;</strong>
                                            <span>{{ v }}</span>
                                        </li>
                                    </ul>
                                </div>

                            </div>
                        </article>
                    </div>
                </div>
            </div>

        </div>
    </div>


</template>

<script>

const trackDetails = {
    t1: {
        id: 1,
        name: "Shot In The Dark",
        album: "Power Up",
        artist: "AC/DC",
        img: "https://static1.abc.es/media/cultura/2020/09/30/powerup-1-U35512706716Llf-620x349@abc.jpg",
        src: "No hay URL",
        duration_ms: 3600
    },
    t2: {
        id: 2,
        name: "Livin' On The Edge",
        album: "Get A Grip",
        artist: "Aerosmith",
        img: "https://www.infobae.com/new-resizer/kx9BdL1rrJnOaMiKMM9agfhc2qo=/768x432/filters:format(jpg):quality(85)/s3.amazonaws.com/arc-wordpress-client-uploads/infobae-wp/wp-content/uploads/2017/09/26134245/Aerosmith.jpg",
        src: null,
        duration_ms: 3600
    },
    t3: {
        id: 3,
        name: "Rocket Queen",
        album: "Apetite For Destruction",
        artist: "Guns N' Roses",
        img: "https://upload.wikimedia.org/wikipedia/commons/thumb/a/a3/GNR_London_Stadium_2017_3_%28cropped%29.jpg/300px-GNR_London_Stadium_2017_3_%28cropped%29.jpg",
        src: "No hay URL",
        duration_ms: 3600
    }
};

export default {

    components: {},

    data() {
        return { 
            track: {}
        }
    },

    // Podemos configurar cierta data que es necesario cambiar en cada página, por ejemplo, el titulo de la pestaña, meta, descripción, etc.
    head() {

        return {
            title: this.track.name
        }

    },

    // En el caso de Nuxt, podemos usar este método que va a reicibir un objeto que contendrá los parámetros de la URL
    asyncData({ params }) {

        const id = params.id;

        // Tiene que retornar una promise que retorne algo que pueda bindear algo que esté en data
        return new Promise(resolve => {
            // Simulo la petición a la API
            setTimeout(() => {
                resolve(trackDetails[`t${id}`]);
            }, 1000);
        }).then(res => {

            // Devolvemos un objeto con las propiedades de data que queremos mapear con el valor que le queremos asignar
            return {
                track: res
            }

        })

    }
}
</script>

<style lang="scss" scoped>
.columns {
    margin: 20px;
}
</style>