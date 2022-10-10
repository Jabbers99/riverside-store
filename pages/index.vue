<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
        <NuxtLogo />
        <VuetifyLogo />
      </v-card>
      <v-card>
        <v-card-title class="headline">
          Welcome to the Vuetify + Nuxt.js template
        </v-card-title>
        <v-card-text>
            <div>
                <h1>{{ merchant.business_name }}</h1>
                <h3>
                    <n-link to="/categories">Categories</n-link>
                </h3>
                <category-list :categories="categories"></category-list>
                <h3>
                    <n-link to="/products">Products</n-link>
                </h3>
                <product-list :products="products"></product-list>
            </div>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/product"
          >
            Continue
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>
<script>
import commerce from "~/common/commerce";

export default {
  async asyncData() {
    const merchant = await commerce.merchants.about();
    const { data: categories } = await commerce.categories.list();
    const { data: products } = await commerce.products.list();

    return {
      merchant,
      categories,
      products,
    };
  },
};
</script>