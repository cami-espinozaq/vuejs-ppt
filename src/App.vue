<template>
  <div id="app">
    <ul id="menu">
      <li data-menuanchor="page1" class="active">
        <a href="#page1">Section 1</a>
      </li>
      <li data-menuanchor="page2"><a href="#page2">Section 2</a></li>
      <li data-menuanchor="page3"><a href="#page3">Section 3</a></li>
    </ul>
    <ul class="actions">
      <li>
        <a class="actions-button" href="#" rel="noopener" @click="addSection"
          >Add section</a
        >
      </li>
      <li>
        <a class="actions-button" href="#" rel="noopener" @click="removeSection"
          >Remove section</a
        >
      </li>
      <li>
        <a
          class="actions-button"
          href="#"
          rel="noopener"
          @click="toggleNavigation"
          >Toggle nav</a
        >
      </li>
      <li>
        <a
          class="actions-button"
          href="#"
          rel="noopener"
          @click="toggleScrollbar"
          >Toggle scrollBar</a
        >
      </li>
    </ul>

    <full-page :options="options" id="fullpage">
      <div class="section">
        <h3>Intro to VueJS</h3>
      </div>
      <div class="section">
        <div class="slide">
          <slide-one></slide-one>
        </div>
        <div class="slide">
          <slide-two></slide-two>
        </div>
        <div class="slide">
          <slide-three></slide-three>
        </div>
        <div class="slide">
          <slide-four></slide-four>
        </div>
      </div>
      <div class="section">
        <div class="slide">
          <h3>Examples using Vue 2</h3>
        </div>
        <div class="slide">
          <slide-five></slide-five>
        </div>
      </div>
    </full-page>
  </div>
</template>

<script>
import SlideOne from './components/SlideOne.vue';
import SlideTwo from './components/SlideTwo.vue';
import './assets/styles/code.css';
import SlideThree from './components/SlideThree.vue';
import SlideFour from './components/SlideFour.vue';
import SlideFive from './components/SlideFive.vue';

export default {
  components: { SlideOne, SlideTwo, SlideThree, SlideFour, SlideFive },
  name: 'app',
  data() {
    return {
      options: {
        licenseKey: 'YOUR_KEY_HERE',
        afterLoad: this.afterLoad,
        scrollOverflow: true,
        scrollBar: false,
        menu: '#menu',
        navigation: true,
        anchors: ['page1', 'page2', 'page3'],
        sectionsColor: [
          '#41b883',
          '#ff5f45',
          '#0798ec',
          '#fec401',
          '#1bcee6',
          '#ee1a59',
          '#2c3e4f',
          '#ba5be9',
          '#b4b8ab',
        ],
      },
    };
  },
  methods: {
    afterLoad() {
      console.log('After load');
    },

    addSection(e) {
      e.preventDefault();
      var newSectionNumber =
        document.querySelectorAll('.fp-section').length + 1;

      // creating the section div
      var section = document.createElement('div');
      section.className = 'section';
      section.innerHTML = `<h3>Section ${newSectionNumber}</h3>`;

      // adding section
      document.querySelector('#fullpage').appendChild(section);

      // creating the section menu element
      var sectionMenuItem = document.createElement('li');
      sectionMenuItem.setAttribute(
        'data-menuanchor',
        'page' + newSectionNumber
      );
      sectionMenuItem.innerHTML = `<a href="#page${newSectionNumber}">Section${newSectionNumber}</a>`;

      // adding it to the sections menu
      var sectionsMenuItems = document.querySelector('#menu');
      sectionsMenuItems.appendChild(sectionMenuItem);

      // adding anchor for the section
      this.options.anchors.push(`page${newSectionNumber}`);

      // we have to call `update` manually as DOM changes won't fire updates
      // requires the use of the attribute ref="fullpage" on the
      // component element, in this case, <full-page>
      // ideally, use an ID element for that element too
      this.$refs.fullpage.build();
    },
    removeSection() {
      var sections = document
        .querySelector('#fullpage')
        .querySelectorAll('.fp-section');
      var lastSection = sections[sections.length - 1];

      // removing the last section
      lastSection.parentNode.removeChild(lastSection);

      // removing the last anchor
      this.options.anchors.pop();

      // removing the last item on the sections menu
      var sectionsMenuItems = document.querySelectorAll('#menu li');
      var lastItem = sectionsMenuItems[sectionsMenuItems.length - 1];
      lastItem.parentNode.removeChild(lastItem);
    },
    toggleNavigation() {
      this.options.navigation = !this.options.navigation;
    },
    toggleScrollbar() {
      console.log('Changing scrollbar...');
      this.options.scrollBar = !this.options.scrollBar;
    },
  },
};
</script>

<style>
a {
  color: #42b983;
}
</style>
