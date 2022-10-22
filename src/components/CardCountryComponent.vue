<template>
  <div>
    <b-row class="mt-3">
      <b-card>
        <b-row>
          <b-col cols="12">
            <b-form-input
              id="input-1"
              v-model="search"
              type="email"
              placeholder="Search country"
              required
              class="mb-2"
            ></b-form-input>
          </b-col>
          <b-col cols="3" v-for="(item, index) in items" v-bind:key="index">
            <b-card
              :id="item.idd.suffixes"
              tag="article"
              style="height: 18rem; width: 14rem; font-size: 13px"
            >
              <b-card-img
                :src="item.flags.svg"
                alt="Image"
                class="rounded-0"
                style="height: 9rem; font-size: 10px"
              ></b-card-img>
              <br />
              <b-card-text>
                <br />
                <b>{{ item.name.common }}</b> <br />
                <b>Population:</b> {{ item.population }} <br /><b>Region:</b>
                {{ item.region }} <br />
                <b>Capital:</b> item.capital
              </b-card-text>
            </b-card>

            <br />
          </b-col>
        </b-row>
      </b-card>
    </b-row>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "CardCountryComponent",
  data() {
    return {
      // Note 'isActive' is left out and will not appear in the rendered table
      search: "",
      countries: [],
    };
  },
  mounted() {
    this.getCustomerData();
  },
  methods: {
    // showCreateModal() {
    //   this.$refs["create-customer-modal"].show();
    // },
    // closeCreateModal() {
    //   this.$refs["create-customer-modal"].hide();
    // },
    getCustomerData() {
      axios
        .get("https://restcountries.com/v3.1/all")
        .then((response) => {
          this.countries = response.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  computed: {
    items() {
      return this.countries.filter((item) => {
        return item.name.common
          .toLowerCase()
          .includes(this.search.toLowerCase());
      });
    },
  },
};
</script>

<style>
.action-item:hover {
  cursor: pointer;
}
</style>
