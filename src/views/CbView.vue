<script>
import ButtonCounter from './ButtonCounter.vue';
import BlogPost from './BlogPost.vue';
import Home from './Tabs/home.vue';
import Posts from './Tabs/post.vue';
import Archives from './Tabs/archive.vue';

export default {
  components: {
    ButtonCounter,
    BlogPost,
    Home,
    Posts,
    Archives
  },
  data(){
    return{
      posts:[
        {id:1, title: '제목1'},
        {id:2, title: '제목2'},
        {id:3, title: '제목3'}
      ],
      postFontSize: 1,
      currentTab: 'Home',
      tabs: ['Home', 'Posts', 'Archives'],
      show: true
    }
  }
}
</script>

<template>
  <div class="layout">
    <h1>This is an Components Basics page</h1>
    <ButtonCounter />
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
    </div>
    <h2>Tab</h2>
    <div class="tabs">
      <div class="buttons">
        <button
          v-for="tab in tabs" 
          :key="tab"
          :class="['tab-button', {active : currentTab === tab}]"
          @click="currentTab = tab"
          >{{ tab }}</button>
          <component :is='currentTab'></component>
      </div>
    </div>
    <button @click="show = !show">토글</button>
    <Transition>
      <p v-if="show">안녕</p>
    </Transition>

    <button @click="show = !show">토글</button>
    <Transition name="slide-fade">
      <p v-if="show">안녕</p>
    </Transition>

    <button @click="show = !show">토글</button>
    <Transition name="bounce">
      <p v-if="show" style="text-align: center;">
        안녕 여기에 탄력적인 텍스트가 있어요
      </p>
    </Transition>

    <button @click="show = !show">토글</button>
    <Transition :duration="550" name="nested">
      <div v-if="show" class="outer">
        <div class="inner">
          안녕
        </div>
      </div>
    </Transition>


  </div>
</template>

<style>
.buttons button{
  opacity: 0.5;
  padding: 10px;
}

.buttons button.active{
  opacity: 1;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}

.bounce-enter-active {
  animation: bounce-in 0.5s;
}
.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}

.outer, .inner {
	background: #eee;
  padding: 30px;
  min-height: 100px;
}
  
.inner { 
  background: #ccc;
}
  
.nested-enter-active .inner,
.nested-leave-active .inner {
  transition: all 0.3s ease-in-out;
}

.nested-enter-from .inner,
.nested-leave-to .inner {
  transform: translateX(30px);
  opacity: 0;
}

.nested-enter-active .inner {
  transition-delay: 0.25s;
}

.nested-enter-from .inner,
.nested-leave-to .inner {
  transform: translateX(30px);
  opacity: 0.001;
}

</style>
