<template>
  <HeaderCont />
  <main id="main">
    <TitleCont name1="movie" name2="book" />
    <section className="movie__cont">
      <div className="container">
        <div className="movie__inner">
          <div class="movie__search">
            <form @submit.prevent="SearchMovies()">
              <div>
                <label for="search" class="sr-only">검색하기</label>
                <input
                  type="search"
                  id="search"
                  placeholder="검색하기"
                  v-model="search"
                />
                <button type="submit">검색</button>
              </div>
            </form>
          </div>
          <div className="movie__list">
            <ul>
              <li className="movieList" v-for="movie in movies" :key="movie.id">
                <a :href="`https://www.themoviedb.org/movie/${movie.id}`">
                  <img
                    :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`"
                    :alt="movie.title"
                  />
                  <span className="title">{{ movie.title }}</span>
                </a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>
    <ContactCont />
  </main>
  <FooterCont />
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import ContactCont from "@/components/ContactCont.vue";
import { ref } from "vue";

export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
  },

  setup() {
    const movies = ref([]);
    const search = ref("");

    const SearchMovies = () => {
      var requestOptions = {
        method: "GET",
        redirect: "follow",
      };

      if (search.value != "") {
        fetch(
          `https://api.themoviedb.org/3/search/movie?api_key=7a86d6b668b870ef5a81078a50ad5826&query=${search.value}`,
          requestOptions
        )
          .then((response) => response.json())
          .then((data) => {
            movies.value = data.results;
            search.value = "";
            console.log(movies);
          })
          .catch((error) => console.log("error", error));
      }
    };

    SearchMovies();

    return {
      movies,
      search,
      SearchMovies,
    };
  },
};
</script>

<style lang="scss" scoped>
.movie__inner {
  font-family: var(--sub_font);
  color: #030406;
  // opacity: 0;
  // transform: translateY(100px);
}

.movie__list {
  ul {
    display: flex;
    flex-wrap: wrap;
    // gap: 24%;
    justify-content: space-evenly;

    .movieList {
      width: 24%;

      .title {
        font-size: 16px;
        font-family: var(--subKor_font);
        display: block;
        padding: 2% 0;
        margin-bottom: 3%;
      }
    }
  }
}
.movie__search {
  position: relative;
  h2 {
    color: var(--white);
    font-size: 40px;
    font-family: var(--subKor_font);
    text-indent: -9999px;
    width: 0;
    height: 0;
  }
  input {
    border: 2px solid var(--light_border);
    width: 100%;
    background: var(--black);
    border-radius: 50px;
    padding: 1rem 3rem 1rem 2rem;
    color: var(--light_bg);
    font-family: var(--subKor_font);
    margin: 0 1%;
    margin-bottom: 5%;
  }
  button {
    position: absolute;
    right: 14px;
    top: 9px;
    background: transparent;
    border: 0;
    color: var(--black);
    background: var(--white);
    font-family: var(--subKor_font);
    width: 40px;
    height: 40px;
    border-radius: 50%;
    font-size: 12px;
    transition: opacity 0.3 ease;

    &:active {
      opacity: 0.7;
    }
  }
}
</style>
