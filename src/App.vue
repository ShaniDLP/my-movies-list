<template>
  <div id="app">
    <header class="app-header">
      <h1>Top 20 Most Popular Movies</h1>
    </header>
    <div v-if="error" class="error-message">
      <p>{{ error }}</p>
    </div>
    <div class="movie-list">
      <MovieItem
        v-for="(movie, index) in movies"
        :key="movie.id"
        :title="movie.title"
        :releaseDate="movie.release_date"
        :posterPath="movie.poster_path"
        :voteAverage="movie.vote_average"
        :voteCount="movie.vote_count"
        :index="index"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import MovieItem from "./components/MovieItem.vue";

const API_KEY = process.env.VUE_APP_API_KEY;
const API_POPULAR_MOVIES = "https://api.themoviedb.org/3/movie/popular";

export default {
  name: "App",
  components: {
    MovieItem,
  },
  data() {
    return {
      movies: [],
      error: null,
    };
  },
  mounted() {
    this.fetchMovies();
  },
  methods: {
    async fetchMovies() {
      try {
        const params = {
          api_key: API_KEY,
          page: 1,
        };
        const response = await axios.get(API_POPULAR_MOVIES, { params });

        this.movies = response.data.results
          .slice(0, 20)
          .sort(
            (lowRating, highRating) =>
              highRating.vote_average - lowRating.vote_average
          );
      } catch (error) {
        console.error("Error fetching movies:", error);
        this.error = "Failed to load movies. Please try again later.";
      }
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Mulish:ital,wght@0,200..1000;1,200..1000&display=swap");

#app {
  font-family: "Mulish", sans-serif;
  text-align: center;
  color: #333;
  min-height: 100vh;
  background: linear-gradient(
    to bottom,
    rgb(146, 199, 207),
    rgb(170, 215, 217)
  );
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.app-header {
  padding: 20px;
  background: linear-gradient(to right, rgb(170, 215, 217), rgb(251, 249, 241));
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
}

.movie-list {
  display: flex;
  gap: 20px;
  flex-direction: column;
  align-items: center;
}

.error-message {
  color: #ff6347;
  font-weight: bold;
  margin: 20px;
  font-size: 48px;
}
@media (max-width: 768px) {
  .app-header {
    padding: 10px;
    font-size: 1.2rem;
  }
  .movie-list {
    gap: 10px;
    padding: 0 10px;
  }
  .error-message {
    font-size: 24px;
  }
}
</style>
