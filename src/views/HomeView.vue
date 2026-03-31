<script setup>
    import {
        useMovieStore
    } from '../stores/movie'

    const movieStore = useMovieStore();
</script>

<template>
    <div class="home">
        <div class="featured-movie-card">
            <router-link to="/movie/tt2016894">
                <img src="/images/movie-img.png" alt="movie-img" class="featured-movie-image" />

                <div class="movie-detail">
                    <h2>Ek Tha Tiger</h2>
                    <p>
                        A RAW agent, Tiger, is sent to Dublin to observe an Indian scientist who is
                        suspected of sharing nuclear secrets with the ISI. He meets and falls for his
                        caretaker Zoya, a girl with a dark secret.
                    </p>
                </div>
            </router-link>
        </div>

        <div class="search-box">
            <form @submit.prevent="movieStore.SearchMovies">
                <div class="form-group">
                    <input type="text" placeholder="Search here" v-model="movieStore.search">

                    <input type="submit" value="Search" />
                </div>
            </form>
        </div>

        <div class="movie-list">
            <div class="movie" v-for="movie in movieStore.movies" :key="movie.imdbID">
                <router-link to="/movie/tt2016894" class="movie-link">
                    <div class="movie-image">
                        <img :src="movie.Poster"
                            alt="movie-img" class="featured-movie-image" />
                        <div class="movie-type">{{ movie.Type }}</div>
                    </div>

                    <div class="movie-detail">
                        <p class="movie-year">{{ movie.Year }}</p>
                        <h2>{{ movie.Title }}</h2>
                    </div>
                </router-link>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
    .home {
        .featured-movie-card {
            position: relative;


            .featured-movie-image {
                width: 100%;
                height: 100%;
                object-fit: cover;
                position: relative;
                z-index: 0;
            }

            .movie-detail {
                position: absolute;
                right: 0;
                left: 0;
                bottom: 0;
                background-color: rgba($color: #000000, $alpha: 0.6);
                padding: 15px;
                z-index: 1;

                h2 {
                    color: #fff;
                    font-size: 24px;
                    margin-bottom: 10px;
                }

                p {
                    color: #f5f5f5;
                }
            }

        }

        .search-box {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 20px;

            .form-group input {
                display: block;
                appearance: none;
                border: none;
                background: none;
                outline: none;

                &[type="text"] {
                    background-color: transparentize($color: #000000, $amount: 0.1);
                    color: #fff;
                    font-size: 16px;
                    padding: 10px 15px;
                    border-radius: 6px;
                    margin-bottom: 10px;

                    &::placeholder {
                        color: #f3f3f3;
                        font-size: 16px;
                    }

                    &:focus {
                        box-shadow: 0px 0px 6px rgba($color: #34D999, $alpha: 0.1);
                    }
                }

                &[type="submit"] {
                    width: 100%;
                    max-width: 300px;
                    font-size: 14px;
                    font-weight: 600;
                    background-color: #34D999;
                    padding: 10px 16px;
                    border-radius: 6px;
                    color: #fff;
                    text-transform: uppercase;
                    transition: 0.4s;

                    &:active {
                        background-color: #1a9968;
                    }
                }
            }
        }

        .movie-list {
            display: flex;
            flex-wrap: wrap;
            gap: 16px;
            padding: 10px;


            .movie {
                width: calc(25% - 16px);
                margin: 0; // আগের margin remove

                .movie-link {
                    display: flex;
                    flex-direction: column;
                    height: 100%;

                    .movie-image {
                        position: relative;
                        display: block;

                        img {
                            display: block;
                            width: 100%;
                            height: 300px;
                            object-fit: cover;
                        }

                        .movie-type {
                            position: absolute;
                            padding: 8px 15px;
                            background-color: #34D999;
                            color: #fff;
                            bottom: 10px;
                            left: 0;
                            text-transform: capitalize;
                        }
                    }

                    .movie-detail {
                        background-color: #1e293b;
                        padding: 10px 15px;
                        flex: 1 1 100%;
                        border-radius: 0px 0px 8px 8px;

                        .movie-year {
                            color: #aaa;
                            font-size: 14px;
                            margin-bottom: 10px;
                        }

                        h2 {
                            color: #fff;
                            font-size: 18px;
                            font-weight: 600;
                        }
                    }
                }
            }
        }
    }
</style>
