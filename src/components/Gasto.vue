<script setup>

    import { formatearCantidad, formatearFecha } from '../helpers';
     import IconoAhorro from '../assets/img/icono_ahorro.svg'
    import IconoCasa from '../assets/img/icono_casa.svg'
    import IconoComida from '../assets/img/icono_comida.svg'
    import IconoGastos from '../assets/img/icono_gastos.svg'
    import IconoOcio from '../assets/img/icono_ocio.svg'
    import IconoSalud from '../assets/img/icono_salud.svg'
    import IconoSuscripciones from '../assets/img/icono_suscripciones.svg';

    const diccionarioIconos = {
        ahorro : IconoAhorro,
        comida : IconoComida,
        casa : IconoCasa,
        gastos : IconoGastos,
        ocio : IconoOcio,
        salud : IconoSalud,
        suscripciones : IconoSuscripciones
    }

    const props = defineProps({
        gasto:{
            type:Object,
            required:true
        }
    });


    defineEmits(['seleccionar-gasto','eliminar-gasto'])
</script>


<template>
    <div class="gasto sombra">
        <div class="contenido">
            <img 
                :src="diccionarioIconos[gasto.categoria]" 
                alt="Icono gasto"
                class="icono"
            >
            <div class="detalles">
                <p class="categoria">{{ gasto.categoria }}</p>
                <p 
                    class="nombre"
                    @click="$emit('seleccionar-gasto', gasto.id)"
                >{{ gasto.nombre }}</p>

                <p class="fecha">
                    Fecha:
                    <span>{{ formatearFecha(gasto.fecha) }}</span>
                </p>
            </div>

        </div>

        <p class="cantidad">{{ formatearCantidad(gasto.cantidad) }}</p>


        <div 
            class="btn-eliminar"
            @click="$emit('eliminar-gasto',gasto.id)"
        >
            <!--!Font Awesome Free v7.2.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2026 Fonticons, Inc.-->
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 640">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 640">
                <path d="M232.7 69.9L224 96L128 96C110.3 96 96 110.3 96 128C96 145.7 110.3 160 128 160L512 160C529.7 160 544 145.7 544 128C544 110.3 529.7 96 512 96L416 96L407.3 69.9C402.9 56.8 390.7 48 376.9 48L263.1 48C249.3 48 237.1 56.8 232.7 69.9zM512 208L128 208L149.1 531.1C150.7 556.4 171.7 576 197 576L443 576C468.3 576 489.3 556.4 490.9 531.1L512 208z"/></svg>
                <path d="M232.7 69.9L224 96L128 96C110.3 96 96 110.3 96 128C96 145.7 110.3 160 128 160L512 160C529.7 160 544 145.7 544 128C544 110.3 529.7 96 512 96L416 96L407.3 69.9C402.9 56.8 390.7 48 376.9 48L263.1 48C249.3 48 237.1 56.8 232.7 69.9zM512 208L128 208L149.1 531.1C150.7 556.4 171.7 576 197 576L443 576C468.3 576 489.3 556.4 490.9 531.1L512 208z"/>
            </svg>
        </div>
    </div>
</template>

<style scoped>
    .gasto{
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-bottom: 2rem;
        position: relative;
        gap: 2rem;
        padding: 3rem;
    }

    @media (min-width:768px){
        .gasto{
            flex-direction: row;
            justify-content: space-between;
            padding: 5rem;
        }
    }

    .contenido{
        display: flex;
        align-items: center;
        gap: 2rem;
    }

    .icono{
        width: 5rem;
    }

    .detalles p{
        margin: 0 0 1rem 0;
    }

    .categoria{
        color: var(--gris);
        font-size: 1.2rem;
        text-transform: uppercase;
        font-weight: 900;
    }

    .nombre{
        color: var(--gris-oscuro);
        font-size: 2.4rem;
        font-weight: 700;
        cursor: pointer;
    }

    .fecha{
        font-size: 1.6rem;
        font-weight: 900;
    }

    .fecha span{
        font-weight: 400;
    }

    .cantidad{
        font-size: 3rem;
        font-weight: 900;
        margin: 0;
    }

    .btn-eliminar{
        width: 3rem;
        fill: red;
        cursor: pointer;
        position: absolute;
        /* top: 0; */
        right: 2rem;
        top: 2rem;
        z-index: 2;
    }
</style>