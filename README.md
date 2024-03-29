# react_tailwindcss_plus_react_the_beginner_guide

### Docs
- deployed version of example: https://tailwindcss-shoes-self.vercel.app/
- tailwind official document: https://tailwindcss.com/docs
- tailwind css tester: https://play.tailwindcss.com/

#### grid
- grid grid-cols-3: flex한 상태로 한줄에 3개씩만 표시

### tailwind breakpoint
- sm: 640px
- md: 768px
- lg: 1004px
- xl: 1280px
- zxl: 1536px

```
<div class="text-4xl">
  <div class="">base</div>
  <div class="invisible sm:visible md:text-red-500 lg:text-8xl">sm: 640px</div>
  <div class="invisible md:visible">md: 768px</div>
  <div class="invisible lg:visible">lg: 1004px</div>
  <div class="invisible xl:visible">xl: 1280px</div>
  <div class="invisible 2xl:visible">2xl: 1536px</div>
</div>

<div class="flex flex-col text-4xl sm:flex-row">
  <div class="">base</div>
  <div class="">sm: 640px</div>
  <div class="">md: 768px</div>
  <div class="">lg: 1004px</div>
  <div class="">xl: 1280px</div>
  <div class="">2xl: 1536px</div>
</div>
```

### state 
- always last element will be applied
```
<button class="m-4 bg-indigo-500 text-white">Click me!</button>
<button class="ml-4 mr-4 mb-4 mt-4 bg-indigo-500 text-white">Click me!</button>
<button class="m-4 px-4 bg-indigo-500 text-white">Click me!</button>
<button class="m-4 rounded-md bg-indigo-500 text-white">Click me!</button>
<button class="focus:ring-2 ring-green-500 bg-red-500 m-4 hover:bg-red-600 active:bg-red-400 rounded-md text-white sm:bg-indigo-500 sm:hover:bg-indigo-600 sm:active:bg-indigo-400">Click me!</button>

<!-- Last element will be applied in the class -->
<ul>
  <li class="first:bg-green-400 last:bg-blue-400 odd:bg-purple-400 even:bg-yellow-300">Element 1</li>
  <li class="first:bg-green-400 last:bg-blue-400 odd:bg-purple-400 even:bg-yellow-300">Element 2</li>
  <li class="first:bg-green-400 last:bg-blue-400 odd:bg-purple-400 even:bg-yellow-300">Element 3</li>
</ul>
```
