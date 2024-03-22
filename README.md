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
