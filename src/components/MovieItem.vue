<template>
  <div class="movie-item">
    <img :src="posterUrl" :alt="title" class="movie-poster" />
    <div class="movie-details">
      <h3>{{ placeNumber }}. {{ title }}</h3>
      <p>Release Date: {{ releaseDate }}</p>
      <div class="movie-rating">
        <svg
          height="16px"
          width="16px"
          version="1.1"
          id="Capa_1"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          viewBox="0 0 53.867 53.867"
          xml:space="preserve"
        >
          <polygon
            style="fill: #efce4a"
            points="26.934,1.318 35.256,18.182 53.867,20.887 40.4,34.013 43.579,52.549 26.934,43.798 
      10.288,52.549 13.467,34.013 0,20.887 18.611,18.182 "
          />
        </svg>
        <span>{{ formattedVoteAverage }} ({{ formattedVoteCount }})</span>
      </div>
    </div>
  </div>
</template>

<script>
const API_IMAGE = "https://image.tmdb.org/t/p/w500";

export default {
  name: "MovieItem",
  props: {
    title: String,
    releaseDate: String,
    posterPath: String,
    voteAverage: Number,
    voteCount: Number,
    index: Number,
  },
  computed: {
    posterUrl() {
      return this.posterPath ? `${API_IMAGE}${this.posterPath}` : null;
    },
    formattedVoteAverage() {
      return this.voteAverage ? this.voteAverage.toFixed(1) : "N/A";
    },
    formattedVoteCount() {
      return this.voteCount
        ? this.voteCount > 1000
          ? "1K+"
          : this.voteCount
        : "N/A";
    },
    placeNumber() {
      return this.index + 1;
    },
  },
};
</script>

<style scoped>
.movie-item {
  display: flex;
  align-items: center;
  height: 150px;
  margin: 8px;
  padding: 16px;
  background: linear-gradient(
    to bottom,
    rgba(251, 249, 241, 0.9),
    rgba(229, 225, 218, 0.9)
  );
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 800px;
  max-width: 100%;
}

.movie-poster {
  border-radius: 8px;
  transition: transform 0.3s ease-in-out;
  height: 100%;
  margin-right: 20px;
}
.movie-poster:hover {
  cursor: pointer;
  transform: scale(1.1);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
}

.movie-details {
  flex: 1;
  text-align: left;
}
.movie-details h3 {
  font-weight: 700;
}

.movie-details p {
  font-weight: 400;
}
.movie-rating {
  display: flex;
  align-items: center;
  justify-content: left;
  margin-top: 10px;
}

.movie-rating svg {
  margin-right: 5px;
}
</style>
