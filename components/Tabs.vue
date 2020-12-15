<template>
        <component-tabs title="Tiêu đề của tabs">
            <ul class="tabs">
                <li v-for="(item, index) in tabsHeader" v-bind:key="index" 
                    v-bind:class="{active: tabActive == index}"
                    v-on:click="setActiveTab(index)">{{item.text}}</li>
            </ul>
            <div class="tab_content tab1" v-if="tabActive === 0">
                 <p>Lorem ipsum dolor</p>
            </div>
            <div class="tab_content tab2" v-if="tabActive === 1">
                 <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ex suscipit, cupiditate voluptatum facere, quis quibusdam, velit impedit nisi veritatis explicabo cumque at. Facere blanditiis quisquam dolorum, itaque consequuntur, sequi distinctio assumenda! Nisi laboriosam fugit, aliquid esse amet itaque consequuntur ratione?</p>

            </div>
            <div class="tab_content tab3" v-if="tabActive === 2">
                 <p>Lorem ipsum dolor</p>
            </div>
        </component-tabs>
</template>

<script>
import ComponentTabs from './ComponentTabs.vue';
export default {
    name: 'tabs',
    data() {
        return {
            tabsHeader: [
                {text:'Tab 1'},
                {text:'Tab 2'},
                {text:'Tab 3'},
            ],
            tabActive: 0
        }
    },
    components: 
    {
        ComponentTabs,
    },
    methods: {
        setActiveTab(index){
            this.tabActive = index;
        }
    }
}
</script>

<style>
html {
  height: 100%;
  font-size: 100%;
}

body {
  background-color: #DBE4AF;
  font: 14px/20px Arial, Tahoma, Verdana, sans-serif;
  width: 100%;
  height: 100%;
  color: #000;
}

* {
  margin: 0;
  padding: 0;
  outline: none;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

.tabs {
  margin: 0;
  padding: 0;
  list-style: none;
  overflow: hidden;
  
}

.tabs li {
  float: left;
  border: 1px solid #999;
  border-bottom: none;
  background: #e0e0e0;
}

.tabs li {
  display: block;
  padding: 10px 20px;
  font-size: 16px;
  color: #000;
  text-decoration: none;
}

.tabs li:hover {
  background: #ccc;
  cursor: pointer;
}

.tabs li.active,
.tabs li.active:hover {
  font-weight: bold;
  background: #fff;
}

.tab_container {
  border-top: none;
     max-width: 990px;
    margin: 0 auto;
    margin-top: 100px;
}

.tab_content {
  padding: 20px;
  font-size: 16px;
   background: #fff;
   border: 1px solid #999;
}
</style>