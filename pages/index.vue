<script setup lang="ts">
import {useStore} from "~/stores";

definePageMeta({
  layout: "main",
  name: "index",
});

const store = useStore();

const {data} = await useFetch('http://localhost:3800/all')

const people = [
  {name: 'Lindsay Walton', title: 'Front-end Developer', email: 'lindsay.walton@example.com', role: 'Member'},
  // More people...
]

</script>


<template>
 <div class="container mx-auto">
   <div class="px-4 sm:px-6 lg:px-8">

     {{ data.data.meta }}

     <div class="grid grid-cols-3 gap-8">
       <div class="border p-10">
         <h1 class="text-lg">Total Companies</h1>
         <span class="font-semibold text-2xl">     {{ data.data.meta.total }}</span>
       </div>
       <div class="border p-10">
         <h1 class="text-lg">Total Companies</h1>
         <span class="font-semibold text-2xl">     {{ data.data.meta.total }}</span>
       </div>
       <div class="border p-10">
         <h1 class="text-lg">Total Companies</h1>
         <span class="font-semibold text-2xl">     {{ data.data.meta.total }}</span>
       </div>

     </div>
     <div class="sm:flex sm:items-center">
       <div class="sm:flex-auto">
         <h1 class="text-base font-semibold leading-6 text-gray-900">Users</h1>
         <p class="mt-2 text-sm text-gray-700">A list of all the users in your account including their name, title, email
           and role.</p>
       </div>
       <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
         <button type="button"
                 class="block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">
           Add user
         </button>
       </div>
     </div>
     <div class="mt-8 flow-root">
       <div class="-mx-4 -my-2 sm:-mx-6 lg:-mx-8">
         <div class="inline-block min-w-full py-2 align-middle">
           <table class="min-w-full border-separate border-spacing-0">
             <thead>
             <tr>
               <th scope="col"
                   class="sticky top-0 z-10 border-b border-gray-300 bg-white bg-opacity-75 py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 backdrop-blur backdrop-filter sm:pl-6 lg:pl-8">
                 Company Name
               </th>
               <th scope="col"
                   class="sticky top-0 z-10 hidden border-b border-gray-300 bg-white bg-opacity-75 px-3 py-3.5 text-left text-sm font-semibold text-gray-900 backdrop-blur backdrop-filter sm:table-cell">
                 town_city
               </th>
               <th scope="col"
                   class="sticky top-0 z-10 hidden border-b border-gray-300 bg-white bg-opacity-75 px-3 py-3.5 text-left text-sm font-semibold text-gray-900 backdrop-blur backdrop-filter lg:table-cell">
                 type_rating
               </th>
               <th scope="col"
                   class="sticky top-0 z-10 border-b border-gray-300 bg-white bg-opacity-75 px-3 py-3.5 text-left text-sm font-semibold text-gray-900 backdrop-blur backdrop-filter">
                 Role
               </th>
               <th scope="col"
                   class="sticky top-0 z-10 border-b border-gray-300 bg-white bg-opacity-75 py-3.5 pl-3 pr-4 backdrop-blur backdrop-filter sm:pr-6 lg:pr-8">
                 <span class="sr-only">Edit</span>
               </th>
             </tr>
             </thead>
             <tbody>
             <tr v-for="(person, personIdx) in data.data.data" :key="person.email">
               <td :class="[personIdx !== people.length - 1 ? 'border-b border-gray-200' : '', 'whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-6 lg:pl-8']">
                 {{ person.organization_name }}
               </td>
               <td :class="[personIdx !== people.length - 1 ? 'border-b border-gray-200' : '', 'whitespace-nowrap hidden px-3 py-4 text-sm text-gray-500 sm:table-cell']">
                 {{ person.town_city }}
               </td>
               <td :class="[personIdx !== people.length - 1 ? 'border-b border-gray-200' : '', 'whitespace-nowrap hidden px-3 py-4 text-sm text-gray-500 lg:table-cell']">
                 {{ person.type_rating }}
               </td>
               <td :class="[personIdx !== people.length - 1 ? 'border-b border-gray-200' : '', 'whitespace-nowrap px-3 py-4 text-sm text-gray-500']">
                 {{ person.route }}
               </td>
               <td :class="[personIdx !== people.length - 1 ? 'border-b border-gray-200' : '', 'relative whitespace-nowrap py-4 pr-4 pl-3 text-right text-sm font-medium sm:pr-8 lg:pr-8']">
                 <a href="#" class="text-indigo-600 hover:text-indigo-900"
                 >Edit<span class="sr-only">, {{ person.name }}</span></a
                 >
               </td>
             </tr>
             </tbody>
           </table>
         </div>
       </div>
     </div>

<!--     <Debug :data="{data}"/>-->
   </div>
 </div>
</template>

