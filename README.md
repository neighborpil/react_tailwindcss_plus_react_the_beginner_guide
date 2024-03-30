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

### Group & peer
- defining the group and peer for it
```
<div class="group border-2 bg-white p-6 hover:bg-sky-500">
  <p class="text-slate-500 group-hover:text-red-500">Create a new project from a variety of starting templates.</p>
  <p class="text-slate-500">Create a new project from a variety of starting templates.</p>
  <p class="text-slate-500 group-hover:text-red-500">Create a new project from a variety of starting templates.</p>

  <div class="bg-purple-400">
      <!-- group style doesn't work because the div doesn't have children-->
      <div class="group h-12 w-12 bg-yellow-500"></div>
      <div class="h-12 w-12 bg-black"></div>
  </div>
  <br />
  <div class="bg-purple-400">
      <div class="peer/yellowSquare h-12 w-12 bg-yellow-500"></div>
      <div class="peer/blackSquare h-12 w-12 bg-black"></div>
      <div class="hidden peer-hover/yellowSquare:block">You are hovering the yellow square</div>
      <div class="hidden peer-hover/blackSquare:block">You are hovering the black square</div>
  </div>
  <br />
  <!-- doesn't work -->
  <div class="bg-purple-400">
      <!-- peer name should be defined before using it-->
      <div class="hidden peer-hover/yellowSquare:block">You are hovering the yellow square</div>
      <div class="hidden peer-hover/blackSquare:block">You are hovering the black square</div>
      <div class="peer/yellowSquare h-12 w-12 bg-yellow-500"></div>
      <div class="peer/blackSquare h-12 w-12 bg-black"></div>
  </div>
  <br />
  <div class="flex flex-col bg-purple-400">
      <!-- but defining the peer name first and reordering it does work-->
      <div class="order-3 peer/yellowSquare h-12 w-12 bg-yellow-500"></div>
      <div class="order-4 peer/blackSquare h-12 w-12 bg-black"></div>
      <div class="order-1 hidden peer-hover/yellowSquare:block">You are hovering the yellow square</div>
      <div class="order-2 hidden peer-hover/blackSquare:block">You are hovering the black square</div>
  </div>
</div>
```
### Theme customize
- uicolor generator: https://uicolors.app/create
- 미리 정해진 클래스만 사용하는 것이 아니라, 커스텀 한 클래스도 따로 css파일을 정의하지 않고 대괄호를 이용해 손쉽게 이용 할 수 있다[]
- config파일에서 테마를 미리 정의하여 사용 할 수 있다
- config
```
/** @type {import('tailwindcss').Config} */
export default {
  theme: {
    extend: {
      colors: {
        mint: '#00d1ad',
        'caribbean-green': {
          DEFAULT: '#00d1ad',
          '50': '#eefffa',
          '100': '#c6fff0',
          '200': '#8effe4',
          '300': '#4dfbd5',
          '400': '#19e8c1',
          '500': '#00d1ad',
          '600': '#00a48c',
          '700': '#028371',
          '800': '#08675b',
          '900': '#0c554b',
          '950': '#003430',
        },
      },
      spacing: {
        "13": "3.25rem"
      }
    },
  },
  plugins: [],
}
```
- html
```
<button class="bg-[#00d1ad] rounded-xl px-[3.2rem] py-2">Button</button>
<button class="bg-[#00d1ad] rounded-[300px] px-[3.2rem] py-2">Button</button>
<button class="bg-mint rounded-[300px] px-[3.2rem] py-2">Button</button>
<button class="bg-caribbean-green-50 rounded-[300px] px-[3.2rem] py-2">Button</button>
<button class="bg-caribbean-green-400 rounded-[300px] px-[3.2rem] py-2">Button</button>
<button class="bg-caribbean-green rounded-[300px] px-[3.2rem] py-2">Button</button>
<!-- px-13 is custom spacing -->
<button class="bg-[#00d1ad] rounded-[300px] px-13 py-2">Button</button>
```
