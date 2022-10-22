<template>
  <div>
    <!-- <b-container class="bv-example-row"> -->
    <b-card no-body class="overflow-hidden">
      <b-row>
        <b-col md="6">
          <b-card-img
            :src="country.flags.svg"
            alt="Image"
            class="rounded-0"
          ></b-card-img>
        </b-col>
        <b-col md="6">
          <b-card-body :title="country.name.common">
            <b-card-text>
              <b-button variant="primary" @click="back()">Back</b-button>
              <br />
              <b>Nombre oficial:</b> {{ country.name.official }}<br />
              <b>Region:</b> {{ country.region }}<br />
              <b>Sub region:</b> {{ country.subregion }}<br />
            </b-card-text>
          </b-card-body>
        </b-col>
      </b-row>
    </b-card>
    <!-- </b-container> -->
  </div>
</template>
<script>
import axios from "axios";

export default {
  name: "DetailCountryComponent",
  data() {
    return {
      // Note 'isActive' is left out and will not appear in the rendered table
      country: null,
    };
  },
  mounted() {
    this.getCountryData();
  },
  methods: {
    // showCreateModal() {
    //   this.$refs["create-customer-modal"].show();
    // },
    // closeCreateModal() {
    //   this.$refs["create-customer-modal"].hide();
    // },
    getCountryData() {
      axios
        .get("https://restcountries.com/v3.1/name/" + this.$route.params.name)
        .then((response) => {
          this.country = response.data[0];
        })
        .catch((error) => {
          console.log(error);
        });
    },
    back() {
      this.$router.replace({ name: "home" });
      // next("/detail");
    },
  },
  computed: {
    items() {
      if (this.selected != null) {
        return this.countries.filter((item) => {
          return item.region
            .toLowerCase()
            .includes(this.selected.toLowerCase());
        });
      }
      return this.countries.filter((item) => {
        return item.name.common
          .toLowerCase()
          .includes(this.search.toLowerCase());
      });
    },
  },
};
</script>
