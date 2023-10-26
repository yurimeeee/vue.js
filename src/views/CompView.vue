<script>
import ButtonCounter from './ButtonCounter.vue';
import BlogPost from './BlogPost.vue';
import HomeView from './Tabs/HomeView.vue';
import PostView from './Tabs/PostView.vue';
import ArchiveView from './Tabs/ArchiveView.vue';

export default {
  components: { //리액트와 달리 임포트 후 사용하기 위해 컴포넌트 등록
    ButtonCounter,
    BlogPost,
    HomeView,
    PostView,
    ArchiveView
  },
  data(){
    return{
      posts:[
        {id:1, title:'제목1'},
        {id:2, title:'제목2'},
        {id:3, title:'제목3'}
      ],
      postFontSize: 1,
      tabs: ['Home', 'Post', 'Archive'],
      currentTab:'Home'
    }
  }
  
}
</script>


<template>
  <div class="layout">
    <h1>This is Components Basics page</h1>
    <ButtonCounter/>
    <ButtonCounter/>
    <ButtonCounter/>
    <!-- 각각 작동하는 독립적인 컴포넌트로 사용 -->

    <hr>
    <h2>Blog</h2>
    <div :style="{ fontSize: postFontSize + 'em' }">
      <BlogPost 
      v-for="post in posts"
      :key="post.id"
      :title="post.title"
      @enlarge-text="postFontSize += 0.1"
      @smaller-text="postFontSize -= 0.1"
      />

      <hr>
      <h2>Tab</h2>
      <div class="tabs">
        <div class="buttons">
          <button 
          v-for="tab in tabs" 
          :key="tab.id" 
          :class="['tab-button', {active:currentTab === tab}]"
          @click="currentTab = tab">
          {{ tab }}
        </button>
        <component :is="currentTab+'View'"></component>
     
        </div>
      </div>
    
    </div>

  </div>
</template>

<style>
  .buttons button{
    padding: 10px;
    opacity: 0.5;
    font-weight: 700;
    background: #fff;
    border: 1.5px solid hsla(160, 100%, 37%, 1);
  }
  .buttons button.active{
    padding: 10px;
    opacity: 1;
    background: hsla(160, 100%, 37%, 1);
    color:#fff
  }

</style>
