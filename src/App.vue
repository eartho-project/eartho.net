<template>
    <div>
        <div class="w-full h-screen bg-[url('https://r2.eartho.net/4.png')] bg-cover bg-center">
            <!-- Overlay -->
            <div class="absolute inset-0 bg-black opacity-50"></div>
            <!-- Overlay Text Center -->
            <!-- https://r2.eartho.net/New_Icon_Eartho2.png -->
            <div class="absolute inset-0 flex items-center justify-center">
                <!-- With Logo -->
                <div class="flex flex-col items-center justify-center p-4">
                    <img src="https://r2.eartho.net/New_Icon_Eartho2.png" class="w-48 h-48 mb-4" alt="Eartho Logo" />
                    <h1 class="text-4xl font-bold text-white">Eartho</h1>
                    <p class="text-xl text-white text-center">
                        เซิร์ฟเวอร์เอาชีวิตรอดภูมิประเทศแบบพื้นโลกสมจริงที่แรกในประเทศไทย
                    </p>
                </div>
            </div>
            <!-- Overlay Read More -->
            <div class="absolute bottom-0 left-0 right-0 flex items-center justify-center">
                <div class="flex flex-col items-center justify-center p-4 text-white animate-bounce">
                    <i class="fas fa-chevron-down"></i>
                </div>
            </div>
        </div>
        <!-- About Me -->
        <div class="container mx-auto p-4 my-10">
            <!-- Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <!-- Left -->
                <div class="flex flex-col items-center justify-center">
                    <img src="https://r2.eartho.net/5.png" class="w-full h-full rounded-lg" alt="Eartho Logo" />
                </div>
                <!-- Right -->
                <div class="flex flex-col items-center justify-center space-y-2">
                    <h1 class="text-4xl font-bold text-gray-800">เกี่ยวกับเซิร์ฟเวอร์</h1>
                    <p class="text-xl text-gray-800 p-4">
                        เซิร์ฟเวอร์เอาชีวิตรอดภูมิประเทศแบบพื้นโลกสมจริงที่แรกในประเทศไทย
                        เป็นโครงการที่นำเสนอโลกเสมือนจริงในรูปแบบเซิร์ฟเวอร์หรือเซิร์ฟเวอร์เกมที่มีลักษณะการเปิดเผยที่เกินกว่าเกมตัวเอง
                        โดยมีการสร้างสรรค์มิติและองค์ประกอบที่คล้ายคลึงกับโลกจริงเพื่อให้ผู้เล่นสามารถมีประสบการณ์ใกล้เคียงกับโลกจริงที่สุด
                        โดยมีความเรียบง่ายและตัวละครที่สามารถปฏิสัมพันธ์กับสิ่งต่างๆ
                        ได้อย่างสมจริง
                        และรวมถึงระบบที่ทันสมัยเพื่อสร้างความคล้ายคลึงในการดำเนินเรื่องราวในเกม
                    </p>
                </div>
            </div>
        </div>
        <!-- Status -->
        <div class="container mx-auto p-4 w-full">
            <div class="flex flex-col items-center justify-center">
                <!-- <h1 class="text-4xl font-bold text-gray-800">สถานะเซิร์ฟเวอร์</h1> -->
                <div class="grid grid-cols-1 md:grid-cols-3 w-full py-4 gap-8">
                    <div>
                        <div class="flex flex-col items-center justify-center">
                            <div class="">
                                <i class="text-6xl fas fa-server"></i>
                            </div>
                            <h1 class="text-2xl font-bold text-gray-800">
                                IP เซิร์ฟเวอร์ / IP Address
                            </h1>
                            <p class="text-xl text-gray-600">play.eartho.net</p>
                        </div>
                    </div>
                    <div>
                        <div class="flex flex-col items-center justify-center">
                            <div class="">
                                <i class="text-6xl fas fa-info"></i>
                            </div>
                            <h1 class="text-2xl font-bold text-gray-800">
                                เวอร์ชั่น / Version
                            </h1>
                            <p class="text-xl text-gray-600">1.20.X</p>
                        </div>
                    </div>
                    <div>
                        <div class="flex flex-col items-center justify-center">
                            <div class="">
                                <i class="text-6xl fas fa-users"></i>
                            </div>
                            <!-- {{ stats }} -->
                            <div v-if="stats && stats.online" class="text-center">
                                <h1 class="text-2xl font-bold text-gray-800">
                                    ออนไลน์ / Online
                                </h1>
                                <p class="text-xl text-green-500">
                                    {{ Number(stats?.players?.online || 0) }}/{{
                                        Number(stats?.players?.max || 0)
                                    }}
                                    Player(s)
                                </p>
                            </div>
                            <div v-else-if="stats && !stats.online" class="text-center">
                                <h1 class="text-2xl font-bold text-gray-800">
                                    ออฟไลน์ / Offline
                                </h1>
                                <p class="text-xl text-red-500">0/0 Player(s)</p>
                            </div>
                            <div v-else class="text-center">
                                <h1 class="text-2xl font-bold text-gray-800">
                                    ออนไลน์ / Online
                                </h1>
                                <p class="text-xl text-green-500">กำลังดึงข้อมูล</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <footer class="bg-white rounded-lg shadow dark:bg-gray-900 m-4">
            <div class="w-full max-w-screen-xl mx-auto p-4">
                <span class="block text-sm text-gray-500 sm:text-center dark:text-gray-400">© {{new Date().getFullYear()}}
                    <a href="https://eartho.net" class="hover:underline">Eartho (eartho.net)</a>. All Rights
                    Reserved.</span>
            </div>
        </footer>
    </div>
</template>
<style scoped></style>
<script setup>
import { onMounted } from "vue";
import { initFlowbite } from "flowbite";
import { ref } from "vue";
const stats = ref(null);
function getMCStats() {
    return fetch("https://api.mcstatus.io/v2/status/java/play.eartho.net").then((response) =>
        response.json()
    );
}

onMounted(async () => {
    initFlowbite();
    stats.value = await getMCStats();
});
setInterval(async () => {
    stats.value = await getMCStats();
}, 10000);
</script>
