<template>
  <div class="first_div">
    <article>
      <input type="number" ref="price_input"/>
      <button @click="update_max_price">Click me</button>
    </article>

    <article v-for="item in items" :key="item[`id`]">
      <div v-if="item[`price`] <= max_price">
        <h2>{{ item[`title`] }}</h2>
        <h3>${{ item[`price`] }}</h3>
        <p>{{ item[`description`] }}</p>
        <img :src="item[`img_url`]" alt="" />
      </div>
    </article>

    <article class="chosen_item"></article>
  </div>
</template>

<script>
export default {

    methods: {
        update_max_price() {
            this.max_price = this.$refs[`price_input`][`value`];
        }
    },

  data() {
    return {
      max_price: 10000,
      items: [
        {
          title: `Vue Warmup`,
          price: 4000,
          description: `some text here to describe the warmup`,
          img_url: `https://s3.eu-west-1.amazonaws.com/redsys-prod/articles/eac8c6d69d1ce8ce0ff8824d/images/teaserImage_xxxx_croppedTeaserImage.jpg`,
          id: `01`,
        },
        {
          title: `Second Vue Warmup`,
          price: 3000,
          description: `some text here to describe the warmup`,
          img_url: `https://cdnp2.stackassets.com/b1284961a6fbcbcfabe6f69c2ae4219ff6daa5e0/store/opt/596/298/1ca89e578fc4e326fe08196758c1688929acc8c5eeb8572e2282628cad78/product_30565_product_shot_wide.jpg`,
          id: `02`,
        },
        {
          title: `Third Vue Warmup`,
          price: 2000,
          description: `some text here to describe the warmup`,
          img_url: `https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRAQxzqZdvZFRp6jPMiQRHPD-ch29hhH9gsF1bu5F2UlHGQN6pVSJETvFgT_Adl3ZsSv6Q&usqp=CAU`,
          id: `03`,
        },
      ],
    };
  },
};
</script>

<style scoped>
.first_div {
  display: grid;
  place-items: center;
  row-gap: 25px;
}

article {
  display: grid;
  grid-auto-flow: row;
  place-items: center;
  text-align: center;
  box-shadow: 8px 8px 16px rgb(217, 217, 217);
  width: 50%;
}

img {
  width: 400px;
  height: 250px;
  object-fit: cover;
}
</style>
