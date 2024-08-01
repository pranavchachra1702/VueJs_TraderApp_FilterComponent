<script setup>
import SearchForm from "./SearchForm.vue";
import FilterDropdown from "./FilterDropdown.vue";
import FilterRadios from "./FilterRadios.vue"
import {computed,ref} from "vue";

const searchFilter = ref('');
const radioFilter = ref('');
const props = defineProps({
    items: {
        type: Array,
        required: true
    }
});

const filteredItems = computed(() => {

    let items = props.items;

    switch(radioFilter.value)
    {
        case 'comedy':
        items = items.filter(item => item.genre.includes("Comedy"));
        break;
        case 'family':
        items = items.filter(item => item.genre.includes("Family"));
        break;
        case 'action':
        items = items.filter(item => item.genre.includes("Action"));
        break;
        case 'adventure':
        items = items.filter(item => item.genre.includes("Adventure"));
        break;
        case 'drama':
        items = items.filter(item => item.genre.includes("Drama"));
        break;
        case 'short':
        items = items.filter(item => item.genre.includes("Short"));
        break;

    }
    if(searchFilter.value != '')
     {
        items = items.filter(item => item.title.includes(searchFilter.value)|| item.creator.includes(searchFilter.value));
     }
    
    return items;

})
const handleSearch = (search) => {
    searchFilter.value = search;

};
const handleRadioFilter = (filter) =>  {
    radioFilter.value = filter;
};
</script>

<template>
<div class="bg-white relative border rounded-lg">
    <div class="flex items-center justify-between">
        <!-- <SearchForm @search="handleSearch"/> -->
        <div class="flex items-center justify-end text-sm font-semibold">
            <FilterRadios @filter="handleRadioFilter"/>
            <FilterDropdown/>
        </div>
        
    </div>
    <table class="w-full text-sm text-left text-gray-500">
        <thead class="text-xs text-gray-700 uppercase bg-gray-50">
            <tr>
                <th class="px-4 py-3">ID</th>
                <th class="px-4 py-3">Title</th>
                <th class="px-4 py-3">Year</th>
                <th class="px-4 py-3">Creator</th>
                <th class="px-4 py-3">Rating</th>
                <th class="px-4 py-3">Genre</th>
                <th class="px-4 py-3">
                    <span class="sr-only">Actions</span>
                </th>
            </tr>
        </thead>
        <tbody>
        <tr v-for="item in filteredItems" :key="item.id" class="border-b">
            <td class="px-4 py-3 font-medium text-gray-900">{{item.id}}</td>
            <td class="px-4 py-3 font-medium text-gray-900">{{item.title}}</td>
            <td class="px-4 py-3 font-medium text-gray-900">{{item.year}}</td>
            <td class="px-4 py-3 font-medium text-gray-900">{{item.creator}}</td>
            <td class="px-4 py-3 font-medium text-gray-900">{{item.rating}}</td>
            <td class="px-4 py-3 font-medium text-gray-900">{{item.genre}}</td>

        </tr>
        </tbody>
    </table>
</div>
</template>