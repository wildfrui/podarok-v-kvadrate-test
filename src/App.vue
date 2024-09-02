<script setup lang="ts">
import { ref } from 'vue'
import Header from './components/Header.vue'

const tabs = [
  { name: '⭐ П Мир 2004783645268' },
  { name: 'В Visa 64549002745' },
  { name: 'В МИР 4657374960' },
]

const currentTab = ref<number>(0);

const transactions = [
  {
    id: 1,
    date: "07.06.2023",
    time: "12:15",
    type: "Траты",
    sum: "-304.00",
    place: "BURGER KING 0794",
    mcc: "5311",
    merchantID: "781000045916"
  },
  {
    id: 2,
    date: "07.06.2023",
    time: "12:15",
    type: "Пополнение",
    sum: "1 584.00",
    place: "BANKRNKOFOODCRD",
    mcc: "5411",
    merchantID: "BANKFOODCRD"
  },
  {
    id: 3,
    date: "07.06.2023",
    time: "12:15",
    type: "Списание за СМС",
    sum: "-99.00",
    place: "BANKRNKOFOODCRD",
    mcc: "5732",
    merchantID: "BANKFOODCRD"
  },
  {
    id: 4,
    date: "07.06.2023",
    time: "12:15",
    type: "Траты",
    sum: "-290.00",
    place: "EVO_KAFE",
    mcc: "5814",
    merchantID: "071000047543"
  },
]

function switchTab(tab: { name: string, current: boolean }) {
  tabs.forEach((t) => {
    tab.current = t === tab;
  })
}
</script>

<template>
  <Header />

  <main>
    <div class="px-8 mt-5 max-w-[1470px] mx-auto">
      <!-- User info -->

      <div class="flex items-start justify-between flex-wrap">
        <div>
          <h1 class="text-2xl tracking-[-0.01em] mr-4 md:mr-0">Иванов Иван Константинович</h1>
          <div class="mt-2 text-base font-medium text-[#757575] flex itemc-center gap-x-4 flex-wrap">
            <div class="flex items-center">
              <span class="mr-1 font-bold">ID</span>
              <span>566534</span>
            </div>
            <div class="flex items-center">
              <span class="mr-1 font-bold">🗒</span>
              <span>Омск</span>
            </div>
            <div class="flex items-center">
              <span class="mr-1 font-bold">📧</span>
              <span>ivanovik@docke.ru</span>
            </div>
          </div>
        </div>
        <div class="mt-4 flex items-center gap-x-4 sm:gap-x-6 md:mt-0">
          <div class="w-[80px] h-[43px] bg-[#AFF4C6] flex items-center justify-center border-4 rounded border-[#8CC39E] sm:w-[119px] sm:h-[43px]">Работает</div>
          <button class="w-[160px] h-[43px] bg-[#FFA629] flex items-center justify-center rounded sm:w-[176px] sm:h-[43px]">✏️ Редактировать</button>
        </div>
      </div>

      <!-- Tabs -->
      <div>
        <button class="mt-2 text-lg text-[#B3B3B3] sm:text-xs sm:mt-0">&lt; назад</button>

        <div class="sm:hidden">
          <select class="mt-2 block w-full rounded-md border-0 py-1.5 pl-3 pr-10 text-black ring-1 ring-inset ring-gray-300 sm:text-sm sm:leading-6">
            <option v-for="(tab, index) in tabs" :key="tab.name" :selected="index === currentTab">{{ tab.name }}</option>
          </select>
        </div>

        <nav class="hidden mt-1 sm:flex" aria-label="Tabs">
          <button v-for="(tab, index) in tabs" :key="tab.name" :class="[index === currentTab ? 'border-black text-black font-bold' : 'border-b-[3px] border-[#D4D4D4] text-[#B3B3B3]', 'flex border-b-[3px] py-[10px] px-[25px] text-base max-w-[250px]']" @click="currentTab = index">{{ tab.name }}</button>
        </nav>

        <span class="mt-8 block text-base font-bold text-black">{{ tabs[currentTab].name }}</span>
        <span class="mt-1 block text-base text-black">Пластиковая Мир - 05/2024</span>

        <div class="mt-2 w-[112px] h-[32px] bg-[#FFCD29] flex items-center justify-center border-4 rounded border-[#CCA421]">Основная</div>

        <div class="mt-8 overflow-hidden">
          <div class="py-4 grid grid-cols-1 max-w-[954px] border-t-[3px] border-[#EEEEEE] sm:grid-cols-[231px_1fr]">
            <div class="flex items-center">
              <span class="text-base text-black block mr-1">Баланс счета</span>
              <div class="group relative flex items-center">
                <button>
                  <img class="w-4 h-4 cursor-pointer hover:" src="./assets/img/info.png" alt="Info image">
                </button>
                <span class="group-hover:opacity-100 transition-opacity bg-[#E6E6E6] p-1 text-[11px] text-[#1E1E1E] rounded-md absolute  opacity-0 m-4 mx-auto min-w-[132px] left-5 top-1">Бвланс, оставшийся на счету</span>
              </div>
            </div>
            <div class=" flex items-center">
              <p class="text-base text-black mr-1 flex items-center">1 003 руб. <span class="text-sm text-[#9F9F9F] block ml-2">(обновлено 07.09.2023 13:56)</span></p>
              <div class="group relative flex items-center">
                <button>
                  <img class="w-4 h-4 cursor-pointer hover:" src="./assets/img/info.png" alt="Info image">
                </button>
                <span class="group-hover:opacity-100 transition-opacity bg-[#E6E6E6] p-1 text-[11px] text-[#1E1E1E] rounded-md absolute  opacity-0 m-4 mx-auto min-w-[132px] left-5 top-1">Данные обновляются
                  один раз в сутки,
                  в будние дни</span>
              </div>
            </div>
          </div>
          <div class="py-4 grid grid-cols-1  max-w-[954px] border-t-[3px] border-[#EEEEEE] sm:grid-cols-[231px_1fr]">
            <div class="flex items-center">
              <span class="text-base text-black block mr-1">Баланс карты</span>
              <div class="group relative flex items-center">
                <button>
                  <img class="w-4 h-4 cursor-pointer hover:" src="./assets/img/info.png" alt="Info image">
                </button>
                <span class="group-hover:opacity-100 transition-opacity bg-[#E6E6E6] p-1 text-[11px] text-[#1E1E1E] rounded-md absolute  opacity-0 m-4 mx-auto min-w-[132px] left-5 top-1">Бвланс, оставшийся на карте</span>
              </div>
            </div>
            <div class="flex items-center">
              <span class="text-base text-black mr-1 flex items-center">1 815 руб.</span>
            </div>
          </div>
          <div class="py-4 grid-cols-1 grid max-w-[954px] border-t-[3px] border-[#EEEEEE] sm:grid-cols-[231px_1fr]">
            <div class="flex items-center">
              <span class="text-base text-black block mr-1">Можно пополнить на</span>
            </div>
            <div class="flex items-center">
              <p class="text-base text-black mr-1 flex items-center">13 997 руб.</p>
            </div>
          </div>
          <div class="py-4 grid grid-cols-1 max-w-[954px] border-t-[3px] border-b-[3px] border-[#EEEEEE] sm:grid-cols-[231px_1fr]">
            <div class="flex items-center">
              <span class="text-base text-black block mr-1">Лимит</span>
            </div>
            <div class="flex items-center">
              <p class="text-base text-black mr-1 flex items-center">8 000 руб./мес.; пн, вт, ср, чт, пт, сб, вс; 08:00-17:00</p>
            </div>
          </div>
        </div>

      </div>

      <!-- Table -->
      <div class="flex flex-col mt-10 mb-8">
        <h2 class="text-2xl tracking-[-0.01em]">История транзакций</h2>

        <button class="mt-2 w-[144px] h-[33px] bg-[#FFA629] flex items-center justify-center rounded lg:self-end lg:mt-0">Скачать .xlsx</button>

        <div class="mt-3">
          <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
            <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
              <div class="overflow-hidden shadow sm:ring-1 sm:ring-black sm:ring-opacity-[0.2] sm:rounded-lg">
                <table class="min-w-full border-spacing-0 sm:rounded-lg">
                  <thead class="bg-[#F4F4F4]">
                    <tr>
                      <th scope="col" class="py-3.5 pl-4 pr-3 text-left text-base font-normal border border-black border-opacity-20 sm:pl-6">N</th>
                      <th scope="col" class="px-3 py-3.5 text-left font-normal text-base border border-black border-opacity-20">Дата</th>
                      <th scope="col" class="px-3 py-3.5 text-left font-normal text-base border border-black border-opacity-20">Время</th>
                      <th scope="col" class="px-3 py-3.5 text-left font-normal text-base border border-black border-opacity-20">Тип транзакции</th>
                      <th scope="col" class="px-3 py-3.5 text-left font-normal text-base border border-black border-opacity-20">Сумма, руб.</th>
                      <th scope="col" class="px-3 py-3.5 text-left font-normal text-base border border-black border-opacity-20">Место</th>
                      <th scope="col" class="px-3 py-3.5 text-left font-normal text-base border border-black border-opacity-20">MCC</th>
                      <th scope="col" class="px-3 py-3.5 text-left font-normal text-base border border-black border-opacity-20">Merchant ID</th>
                    </tr>
                  </thead>
                  <tbody class="divide-y divide-gray-200 bg-white">
                    <tr v-for="(transaction, index) in transactions" :key="index">
                      <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm border border-black border-opacity-20 sm:pl-6">{{ index + 1 }}</td>
                      <td class="whitespace-nowrap px-3 py-4 text-base border border-black border-opacity-20">{{ transaction.date }}</td>
                      <td class="whitespace-nowrap px-3 py-4 text-base border border-black border-opacity-20">{{ transaction.time }}</td>
                      <td class="whitespace-nowrap px-3 py-4 text-base border border-black border-opacity-20">{{ transaction.type }}</td>
                      <td class="whitespace-nowrap px-3 py-4 text-base border border-black border-opacity-20 text-right">{{ transaction.sum }}</td>
                      <td class="whitespace-nowrap px-3 py-4 text-base border border-black border-opacity-20 text-right">{{ transaction.place }}</td>
                      <td class="whitespace-nowrap px-3 py-4 text-base border border-black border-opacity-20 text-right">{{ transaction.mcc }}</td>
                      <td class="whitespace-nowrap px-3 py-4 text-base border border-black border-opacity-20 text-right">{{ transaction.merchantID }}</td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </div>
          </div>
        </div>

        <div class="mt-5 flex flex-col gap-y-4 items-center justify-between sm:flex-row lg:mt-3">
          <div class="flex items-center gap-x-2 text-[#757575] text-sm">
            <input class="w-10 pl-1 bg-[#d5d5d5] rounded" type="number" min="1" max="15" value="10" />
            <span>Записи с 1 по 10 из 36 записей</span>
          </div>

          <div class="flex items-center gap-x-1">
            
            <button class="w-7 h-5 flex items-center text-black justify-center bg-[#e2e2e2]">
              <img class="w-4 h-4" src="./assets/img/chevron-left.svg" alt="Chevron left">
            </button>

            <button v-for="(num, index) in [1, 2, 3, 4, 5]" :class="index === 0 ? 'bg-orange-500 text-white' : 'bg-white text-black'" class="w-5 h-5 flex items-center text-black justify-center">
              {{ num }}
            </button>

            <button class="w-7 h-5 flex items-center text-black justify-center bg-[#e2e2e2]">
              <img class="w-4 h-4" src="./assets/img/chevron-right.svg" alt="Chevron left">
            </button>

            <button class="w-7 h-5 flex items-center text-black justify-center bg-[#e2e2e2]">
              <img class="w-4 h-4" src="./assets/img/chevron-right-double.svg" alt="Chevron left">
            </button>

          </div>
        </div>
      </div>
    </div>
  </main>
</template>
