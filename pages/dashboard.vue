<template>
  <div class="bg-[#EDEAE7] min-h-screen">
    <div class="container mx-auto px-4 py-6">
         <Header />



      <div class="my-8"></div>

      <h2 class="text-xl font-bold mt-8 mb-4 text-[#595959]">Dashboard</h2>

      <div class="flex flex-wrap -mx-4">
        <Card :number="2" text="KIAMBU COUNTY" buttonColor="#F3D052" buttonTextColor="#000000" buttonLabel="Order Feeds" cName="Farms" endpoint="/dashboard"  />
        <Card :number="36" text="LARGE WHITE" buttonColor="#517148" buttonLabel="Sell a Batch" cName="Pigs" endpoint="/submit" />
      </div>

      <h2 class="text-xl font-bold mt-8 mb-4 text-[#595959]">Latest</h2>

      <div class="flex flex-wrap -mx-4">
        <PostCard
          v-for="post in latestPosts"
          :key="post.id"
          :image="post.image"
          :title="post.title"
          :category="post.category"
          :category2="post.category2"
        />
      </div>
    </div>
  </div>
</template>


<script>
import Card from '@/components/Card.vue';
import PostCard from '@/components/PostCard.vue';
import postsData from '../server/api/data.json';
import Header from '@/components/Header.vue';


export default {
  name: 'Dashboard',
  components: {
    Card,
    PostCard,
  },
  data() {
    return {
      pageTitle: 'Nairobi Sausages',
    };
  },
  computed: {
  
    latestPosts() {
      return postsData.posts.slice(0, 5);
    }
  }
};
</script>


