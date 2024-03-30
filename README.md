# react_tailwindcss_plus_react_the_beginner_guide

### Docs
- deployed version of example: https://tailwindcss-shoes-self.vercel.app/
- tailwind official document: https://tailwindcss.com/docs
- tailwind css tester: https://play.tailwindcss.com/
- 강좌 깃 프로젝트: https://github.com/codiku/tailwindcss-shoes
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

### Directives
- css 파일에 커스텀 클래스를 작성하여 전체 파일에서 사용 할 수 있다
- css
```
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  h1 {
    @apply text-4xl font-bold;
  }
  h2 {
    @apply text-2xl font-semibold;
    background-color: red;
  }
  p {
    @apply text-gray-400;
  }
}

@layer components {
  .btn-danger {
    @apply rounded-lg bg-red-500 px-4 py-2 text-white hover:bg-red-600;
  }
}

@layer directives {
  .flex-center {
    @apply flex items-center justify-center;
  }
}
```
- html
```
<h1>Welcome to Our Webstie</h1>

<h2 >Tailwind is pretty dope</h2>
<p>Here: a lot of reasons why tailwind is dope</p>

<h2 >React is pretty dope</h2>
<p>Here: a lot of reasons why React is dope</p>

<h2 >NodeJS is pretty dope</h2>
<p>Here: a lot of reasons why NodeJS is dope</p>

<button class="rounded-lg bg-red-500 px-4 py-2 text-white hover:bg-red-600">Delete</button>
<button class="btn-danger">Danger</button>

<div class="bg-blue-200 h-44 flex items-center justify-center">
  <p>HI</p>
</div>

<div class="bg-blue-200 h-44 flex-center">
  <p>HI</p>
</div>
```

### dark mode
- config에서 darkMode를 정의해줘야 한다. 이후에 html에서 dark:를 붙이고 쓰면 된다
- darkMode를 class로 설정해 두고 아래의 코드를 통해 다크모드를 전환 할 수 있다. 그러면 최상단의 html코드에 dark라는 클래스가 달린다
```
onclick="document.documentElement.classList.toggle('dark')"
```
- config
```
/** @type {import('tailwindcss').Config} */
export default {
  darkMode: "class",
  theme: {
    extend: {
    },
  },
  plugins: [],
}
```
- html
```
<div class="flex h-screen items-center justify-center">
  <div class="rounded-lg bg-white p-6 shadow-lg dark:bg-indigo-950 dark:shadow-sm">
    <h2 class="text-2xl font-semibold text-gray-800 dark:text-white">Card Title</h2>
    <p class="mt-2 text-gray-600 dark:text-gray-400">This is the main content of the card.</p>
    <p class="mt-2 text-gray-400">Subtext or additional information goes here.</p>

    <button onclick="document.documentElement.classList.toggle('dark')" class="mt-4 rounded bg-indigo-500 px-4 py-2 font-semibold text-white hover:bg-indigo-600">Button</button>
  </div>
</div>
```

## Tailwind Shoe project setting
1. tailwindcss 가이드 프로젝트 페이지에서 내용을 확인한다
    + https://tailwindcss.com/docs/guides/vite
2. terminal에서 아래의 코드를 실행하여 프로젝트를 만든다
```
% npm create vite@latest tailwind-shoes -- --template react
% cd tailwind-shoes
% npm install
```

3. tailwindcss를 설치하고 초기화한다
```
% npm install -D tailwindcss postcss autoprefixer
% npx tailwindcss init -p
```

4. webstorm으로 열고 tailwind.cofnig.js파일에서 초기 내용을 가이드페이지처럼 설정해준다
    + tailwind.config.js
```
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

5. 글로벌 index.css에 모든것을 지우고 tailwindcss directives를 추가한다

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

    + 그리고 추가로 초기 프로젝트 설정에서 생긴 App.css파일은 필요없으니 삭제
    + 그리고 App.jsx파일안에서 App.css관련된 내용은 모두 삭제
    + App.jsx
    
```
function App() {
  return (
    "HI!"
  )
}

export default App
```

6. 기타사항
    + main.jsx를 index.jsx로 바꿔준다. 그리고 index.html에서 링크를 index.jsx로 바꾼다
    + vite.config.js파일에서 port설정을 3000으로 바꿔준다
```
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  server: {
    port: 3000,
  }
})
```
    + index.jsx에서 StrictMode제거하고 불필요한 import 제거
    + assets에 이미지 추가
     
7. prettier, svg등  추가

```
% npm install -d prettier prettier-plugin-tailwindcss vite-plugin-svgr
```

    + prettier setting: settings에서 prettier로 검색한 후에 Automatic Prettier configuration과 run on save에 체크
