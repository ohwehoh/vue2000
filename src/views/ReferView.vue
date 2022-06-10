<template>
  <HeaderCont />
  <main id="main">
    <TitleCont name1="referece" name2="book" />
    <section className="refer__cont">
      <div className="container">
        <div className="refer__inner">
          <h2>CSS</h2>
          <ul className="refer__list">
            <li v-for="refer in refers" :key="refer.id">
              <a href="">
                <span className="num">{{ refer.id }}</span>
                <span className="title">{{ refer.title }}</span>
                <span className="desc">{{ refer.desc }}</span>
                <span className="use">{{ refer.use }}</span>
              </a>
            </li>
          </ul>
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
    const refers = ref([]);

    const Reference = () => {
      var requestOptions = {
        method: "GET",
        redirect: "follow",
      };
      fetch(
        "https://webstoryboy.github.io/react2022/src/assets/json/refer.json",
        requestOptions
      )
        .then((response) => response.json())
        .then((data) => (refers.value = data.data.htmlRefer))
        .catch((error) => console.log("error", error));
    };

    setTimeout(() => {
      Reference();
    }, 2000);

    return {
      refers,
      Reference,
    };
  },
};
</script>

<style lang="scss">
.refer__cont {
  font-family: var(--subKor_font);
  min-height: 100vh;
  padding-bottom: 20vw;
}
.refer__inner {
  h2 {
    color: var(--white);
    font-size: 2rem;
    margin-bottom: 1rem;
  }
}

.refer__list {
  border-top: 2px solid var(--light_bg);
  border-bottom: 1px solid var(--light_bg);

  a {
    display: block;
    color: var(--white);

    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid var(--light_bg);
    padding: 1.3rem 0;
    transition: all 0.3s;
    font-family: var(--subKor_font);

    &:hover {
      background: rgba($color: #000, $alpha: 0.7);
      color: var(--black);
    }

    span {
      display: inline-block;
    }
    span:nth-child(1) {
      text-align: center;
      width: 6%;
    }
    span:nth-child(2) {
      width: 20%;
    }
    span:nth-child(3) {
      width: 64%;
    }
    span:nth-child(4) {
      text-align: center;
      width: 10%;
    }
  }
}

.refer__table {
  padding-top: 200px;
  color: var(--white);
  font-family: var(--subKor_font);

  h3 {
    font-size: 3rem;
  }

  .img_p_wrap {
    display: flex;

    img {
      width: 100%;
      height: 20%;
      background-position: center center;
    }

    p {
      background-color: var(--light_bg);
      color: var(--black);
      padding: 1.4em;
    }
  }

  .table {
    color: var(--white);
    font-family: var(--subKor_font);
    border: 1px solid var(--light_bg);
    margin-top: 0.5em;

    tr {
    }

    th,
    td {
      font-weight: normal;
      padding: 1em;
      border-bottom: 1px solid var(--light_bg);
      border-left: 1px solid var(--light_bg);
    }

    td {
      ul {
        li {
          transition: all 0.3s;
          &::before {
            content: "";
            display: inline-block;
            width: 0.5rem;
            height: 0.5rem;
            background: #fff;
            border-radius: 50%;
            margin-right: 0.5rem;
          }
          &:hover {
            color: burlywood;
            &::before {
              background-color: burlywood;
            }
          }
        }
      }
      a {
        display: block;
        transition: all 0.3s;
        &:hover {
          color: burlywood;
        }
      }
    }
  }
}
</style>
