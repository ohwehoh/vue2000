<template>
  <HeaderCont />
  <main id="main">
    <section className="contact">
      <div className="contact__inner">
        <p>YOU ARE</p>
        <p>ALREADY</p>
        <p>DOING WELL.</p>
        <p>
          같은 목표를 위해 달려갈 웹 퍼블리셔 &#38; 프론트 앤드 개발자를
          모집합니다. 관심 있는 분들은 카카오톡 또는 카페에 문의해주세요.
        </p>
      </div>
    </section>
  </main>
  <FooterCont />
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import FooterCont from "@/components/FooterCont.vue";
export default {
  components: {
    HeaderCont,
    FooterCont,
  },
};
</script>

<style lang="scss">
.contact {
  font-family: var(--main_font);
  font-size: 10vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: var(--white);

  .contact__inner {
    width: 90vw;
    margin: 0 auto;

    p {
      // opacity: 0;
      // transform: translateY(100px);

      &:nth-child(1) {
        margin-left: 0vw;
        margin-bottom: -6vw;
      }
      &:nth-child(2) {
        margin-left: 16%;
        margin-bottom: -6vw;
      }
      &:nth-child(3) {
        margin-left: 32%;
      }
      &:nth-child(4) {
        margin-left: auto;
        width: 20vw;
        font-size: 0.8vw;
        font-family: var(--kor_font);
        line-height: 1.8;
        font-weight: 300;
      }
    }
  }
}
</style>
