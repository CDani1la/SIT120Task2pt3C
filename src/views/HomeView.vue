<script setup>
import TheWelcome from '../components/TheWelcome.vue'
import myListComponent from '../components/my-component.vue'
import theComponent from '../components/theComponent.vue'
import Scripts from '../components/Scripts.vue'
import { createApp, ref, reactive, watch } from 'vue';
const message = ref('Hello world');
const htmlContent = '<h1> this is heading text </h1>';
const dynamicId = 'dynamic-element-id';
const title = 'Hello World Vue!';
const count = ref(0);
const aIsActive = ref(false);
const bIsActive = ref(true);
const bgColor = 'grey';
const textColor = 'white';
const isChecked = ref(true);
const radioPicked = ref('none');
const selected = ref('none');
const items = reactive([
                        {id: 1, text: 'Text1', finished:true},
                        {id: 2, text: 'Text2', finished:false},
                        {id: 3, text: 'Text3', finished:true},
                        {id: 4, text: 'Text4', finished:false},
                        {id: 5, text: 'Text5', finished:true},
                        {id: 6, text: 'Text6', finished:false},
            ]);
            const theObject = reactive ({
                        title:"ABC!@#",
                        author:'John smith',
                        publishedAt: '2005-02-23'
            });

// Define methods
const add = () => {
    count.value++;
};
watch(message, (newVal, oldVal) => {
              console.log('Msg changed from ' + oldVal + ' to ' + newVal);
});


</script>

<template>
      <div>
        <h1>In my-component</h1>
        <p v-html="htmlContent"></p>
        <div v-bind:id="dynamicId">{{title}}</div>
        <button @click="add">
                Count: {{ count }}
            </button>
        <div v-bind:class="{a: aIsActive, b: bIsActive}">Binding HTML class</div>
        <div v-bind:style="{ backgroundColor: bgColor, color: textColor }">Styling using v-bind</div>
        <p>an object</p>
        <ul>
            <li v-for="value in theObject">
                {{value}}
            </li>
        </ul>
        <p> a range (from 1 to 3)</p>
        <ul>
            <li v-for="n in 3">{{items[n-1].text}}</li>
        </ul>
        <p>on template with v-if (show finished ids)</p>
        <template v-for="item in items">
            <li  v-if="!item.finished">
                {{ item.text }}
            </li>

        


        
        </template>
        <myListComponent v-for="(item, index) in items"
        :key="index"
        :title="item.text"
        :content="item.finished">
        </myListComponent>
        <button @click="count++">
            Count(inline handler):
        </button>
        <p> {{count}}</p>
        <button @click="add">
            Count(method handler): {{count}}
        </button>
                <!-- text input -->
                <p>Text Input</p>
        <p>Message: {{message}}</p>
        <input v-model="message" placeholder="Edit this">
        <!-- checkbox input -->
        <p>checkbox input</p>
        <input type="checkbox" id="checkbox" v-model="isChecked" />
        <label for="checkbox">{{ isChecked }}</label>
        <!-- radio input -->
        <p>radio input, {{radioPicked}}</p>
        <input type="radio" id="one" value="A" v-model="radioPicked" />
        <label for="one">A</label>

        <input type="radio" id="two" value="B" v-model="radioPicked" />
        <label for="two">B</label>
        <!-- select and text area -->
        <p>selected: {{selected}}</p>
        <select v-model="selected">
            <option>Left</option>
            <option>Right</option>
            <option>Forward</option>
        </select>
        <!-- v-model modifiers[.lazy, .number, .trim] -->
        <p>Message (lazy): {{message}}</p>
        <input v-model.lazy="message" placeholder="Edit this">
        <p>Message (number): {{numb}}</p>
        <input v-model.number="numb" placeholder="Edit this">
        <p>Message (trim): {{message}}</p>
        <input v-model.trim="message" placeholder="Edit this">
        <!-- Attribute Bindings  -->
        <!-- javascript expressions inside syntax "{{}}" -->
        <!-- <div v-bind:id="dynamicId">{{title}}</div> -->
        <theComponent/>
    </div>
    
</template>


