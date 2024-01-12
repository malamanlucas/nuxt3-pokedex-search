<template>
    <div class="main">
        <div class="main__header">
            <div class="main__header__title">
                Pokemons visíveis: 10
            </div>
            <div class="main__header__filter">
                <input type="text" class="main__header__filter__input" />
                <button class="main__header__filter__reset-btn">
                    Reiniciar
                </button>
            </div>
        </div>

        <div class="main__body">
            <div class="main__body__pokemon-list">

                <div v-for="pokemon in pokemons" :key="pokemon.id"
                     class="main__body__pokemon-list__card">
                    <div class="main__body__pokemon-list__card__info">
                        <div class="main__body__pokemon-list__card__info__title">
                            {{ pokemon.id }} - {{ pokemon.nome }}
                        </div>
    
                        <img class="main__body__pokemon-list__card__info__img"
                            :src="pokemon.img" />
                    </div>

                    <button
                        class="main__body__pokemon-list__card__btn"
                    >Excluir</button>
                </div>

            </div>

        </div>
    </div>
</template>

<script setup lang="ts">

interface Pokemon {
    nome: string,
    id: number,
    img: string
}

let pokemon: Pokemon = {
    nome: "Bulbsaur",
    id: 1,
    img: '/bulbsaur.png'
}

var pokemons: Pokemon[] = [pokemon, pokemon, pokemon]

</script>

<style scoped lang="scss">
.main {
    &__header {
        display: flex;
        flex-direction: column;
        align-items: center;
        &__title {
            background: #c62828;
            color: white;
            padding: 10px;
            border-radius: 5px;
            margin-bottom: 20px;
            font-weight: 900;
            font-size: 24px;
            display: flex;
            align-items: center;
        }

        &__filter {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
            &__input {
                padding: 10px;
                font-size: 16px;
                border: 1px solid #f2c94c;
                border-radius: 4px;
                margin-bottom: 10px;
                background-color: #ffcc00; 
                color: #333; 
            }
            &__reset-btn {
                background-color: #1976d2;
                color: white;
                padding: 10px 20px;
                border: none;
                border-radius: 5px;
                cursor: pointer;
                font-size: 16px;
                margin-left: 15px;
            }
        }

    }

    &__body {
        &__pokemon-list {
            display: flex;
            justify-content: center;
            flex-wrap: wrap; /* Permite que os cards quebrem para a próxima linha se não houver espaço suficiente */
            gap: 20px; /* Espaçamento entre os cards */
            &__card {
                padding: 10px;
                border: 1px solid #ccc;
                display: flex;
                flex-direction: column;
                max-width: 300px; /* Largura máxima de cada card */
                &__info {
                    display: flex;
                    flex-direction: column;
                    align-items: center;
                    &__title {
                        background-color: #f2f2f2;
                        padding: 5px;
                        border-radius: 5px;
                        margin-bottom: 5px;
                        text-align: center;
                    }
                    &__img {
                        max-width: 250px;
                        max-height: 250px;
                        margin-left: auto;
                        margin-right: auto;
                        margin-bottom: 10px;
                    }
                }
                &__btn {
                    background-color: #c62828;
                    color: white;
                    font-size: 16px;
                    padding: 10px 15px;
                    border: none;
                    border-radius: 3px;
                    cursor: pointer;
                    transition: background-color 0.3s;
                }
            }
        }
    }
}
</style>