<template>
  <!-- eslint-disable max-len -->
  <section class="section-container">
    <b-container class="section-wrapper">
      <b-row class="justify-content-center section-row">
        <b-col lg="12">
          <div class="text-content">
            <p>
              <sup>1</sup>
              <span>HDR display required</span>
            </p>
            <p>
              <sup>2</sup>
              <span
                >PlayStation®Plus is a paid-for ongoing subscription with a recurring fee charged
                automatically at the frequency chosen by the consumer at purchase until cancelled.
                Users must be over 7 years old and users under 18 require parental consent, except
                that users in Germany must be 18 years or older. Full terms apply, see
                playstation.com/legal.</span
              >
            </p>
            <p>
              <sup>3</sup>
              <span> Netflix subscription sold separately </span>
            </p>
            <p>
              <sup>4</sup>
              <span
                >Subscriptions to streaming services and other entertainment sold separately</span
              >
            </p>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </section>
</template>

<script>
export default {
  // eslint-disable-next-line quotes
  name: "SectionCompoent",
};
</script>

<style lang="scss" scoped>
.section-container {
  background-color: #eeeeee;
  .section-wrapper {
    max-width: 1320px !important;
    padding: 60px 20px;
    .section-row {
      .text-content {
        p {
          margin: 15px 0;
          sup {
            margin-right: 4px;
            font-size: 0.8rem;
          }
          span {
            font-size: 1.3rem;
          }
        }
      }
    }
  }
}
</style>
