<template>
    <div class="min-h-screen bg-gradient-to-r from-blue-100 via-purple-100 to-blue-200 flex flex-col items-center justify-center p-4">
        <div class="about-card bg-white p-6 md:p-10 rounded-lg shadow-2xl text-center transform transition duration-500 hover:scale-105 hover:shadow-3xl w-full max-w-4xl">
            <h1 class="text-4xl md:text-6xl font-extrabold mb-6 text-transparent bg-clip-text bg-gradient-to-r from-blue-300 via-purple-300 to-blue-500 animate-gradient">{{ aboutTitle }}</h1>
            <img src="../public/Chinnapat photo2.JPG" class="w-2/3 md:w-1/3 h-auto mx-auto mb-6 rounded-full border-4 border-blue-200 shadow-lg hover:shadow-2xl transition duration-500 hover:scale-110">
            <p class="text-gray-700 mb-6 text-base md:text-lg leading-relaxed">{{ aboutText1 }}</p>
            <p class="text-gray-700 mb-6 text-base md:text-lg leading-relaxed">{{ aboutText2 }}</p>
            <p class="text-gray-700 mb-6 text-base md:text-lg leading-relaxed">{{ aboutText3 }}</p>
            <p class="text-gray-700 mb-6 text-base md:text-lg leading-relaxed">{{ aboutText4 }}</p>
            <ul class="text-gray-700 text-base md:text-lg mb-6 list-disc list-inside">
                <li>{{ interest1 }}</li>
                <li>{{ interest2 }}</li>
                <li>{{ interest3 }}</li>
                <li>{{ interest4 }}</li>
            </ul>
            <div class="flex flex-wrap justify-center mb-6 space-x-2 md:space-x-4">
                <img src="../public/HTML5.png" alt="HTML5 Logo" class="tech-logo">
                <img src="../public/css.png" alt="CSS Logo" class="tech-logo">
                <img src="../public/ts-js.png" alt="JavaScript Logo" class="tech-logo">
                <img src="../public/Vue.js.png" alt="Vue.js Logo" class="tech-logo">
                <img src="../public/Csharp.png" alt="C# Logo" class="tech-logo">
                <img src="../public/java.png" alt="Java Logo" class="tech-logo">
                <img src="../public/python.png" alt="Python Logo" class="tech-logo">
            </div>
            <h1 class="text-xl md:text-3xl font-bold mb-6 text-blue-300 animate-pulse">{{ buttonText }}</h1>
            <button @click="toggleLanguage" class="bg-gradient-to-r from-blue-300 via-purple-300 to-blue-500 hover:from-blue-500 hover:to-blue-300 text-white font-bold py-2 px-4 md:py-3 md:px-6 rounded-full shadow-lg transform transition duration-300 hover:scale-110 hover:shadow-2xl">{{ buttonLabel }}</button>
        </div>
    </div>
</template>

<script setup>
useHead({
    title: 'About Me',
    meta: [
        {
            name: 'description',
            content: 'About Chinnapat Boonyod'
        },
    ]
})
import { ref } from 'vue'

const count = ref(0)
const language = ref('th')

const aboutTitle = ref('About me')
const aboutText1 = ref('สวัสดีครับ! ผมชื่อ ชินภัทร บุญยศ (Chinnapat Boonyod) ชื่อเล่น ชิน (Chin) ผมเป็นนักเรียนที่หลงใหลในการเขียนโปรแกรม')
const aboutText2 = ref('ผมมีความสนใจในคอมพิวเตอร์มาตั้งแต่เด็ก โดยเฉพาะการเขียนโปรแกรม จุดเริ่มต้นของความสนใจเกิดจากตอนที่เล่นเกมออนไลน์ แล้วสังเกตเห็นว่ามีคนใช้โปรแกรมช่วยเล่น ทำให้ผมอยากรู้ว่ามันทำงานยังไง')
const aboutText3 = ref('เมื่อผมเริ่มศึกษาหาความรู้เกี่ยวกับโปรแกรมมิ่ง ผมก็เริ่มเข้าใจว่ามันคือกระบวนการที่ทำให้โปรแกรมทำตามคำสั่งของผู้ใช้ ความสงสัยในตอนนั้นได้กลายเป็นความหลงใหลในการเขียนโปรแกรมจนถึงวันนี้')
const aboutText4 = ref('ตอนนี้ผมเรียนอยู่ที่ โรงเรียนทวีธาภิเษก, บางขุนเทียน และมีความสนใจในสาขาต่างๆ เช่น:')
const interest1 = ref('การพัฒนาเกม (Game Development)')
const interest2 = ref('การพัฒนาเว็บไซต์แบบ Full Stack (Full Stack Development)')
const interest3 = ref('ปัญญาประดิษฐ์ / การเรียนรู้ของเครื่อง (AI / Machine Learning)')
const interest4 = ref('การตัดต่อภาพและวิดีโอ (Photo / Video Editing)')
const buttonText = ref('Click the button to change language')
const buttonLabel = ref('คลิกปุ่มเพื่อเปลี่ยนภาษา')

const toggleLanguage = () => {
    if (language.value === 'th') {
        language.value = 'en'
        aboutTitle.value = 'About me'
        aboutText1.value = 'Hello! My name is Chinnapat Boonyod, but you can call me Chin. I am a student passionate about programming.'
        aboutText2.value = 'I have been interested in computers since I was young, especially programming. My interest started when I played online games and noticed that people were using programs to assist with gameplay. This made me curious about how it worked.'
        aboutText3.value = 'As I started studying programming, I began to understand that it is a process that allows programs to follow user commands. What was once curiosity has now turned into a passion for programming, and it continues to this day.'
        aboutText4.value = 'Currently, I am studying at Thaveethapisek School, Bangkhunthian, and I am interested in various fields such as:'
        interest1.value = 'Game Development'
        interest2.value = 'Full Stack Development'
        interest3.value = 'Artificial Intelligence / Machine Learning'
        interest4.value = 'Photo / Video Editing'
        buttonText.value = 'Click the button to change language'
        buttonLabel.value = 'Click the button to change language'
    } else {
        language.value = 'th'
        aboutTitle.value = 'เกี่ยวกับฉัน'
        aboutText1.value = 'สวัสดีครับ! ผมชื่อ ชินภัทร บุญยศ (Chinnapat Boonyod) ชื่อเล่น ชิน (Chin) ผมเป็นนักพัฒนาซอฟต์แวร์ที่หลงใหลในการเขียนโปรแกรม'
        aboutText2.value = 'ผมมีความสนใจในคอมพิวเตอร์มาตั้งแต่เด็ก โดยเฉพาะการเขียนโปรแกรม จุดเริ่มต้นของความสนใจเกิดจากตอนที่เล่นเกมออนไลน์ แล้วสังเกตเห็นว่ามีคนใช้โปรแกรมช่วยเล่น ทำให้ผมอยากรู้ว่ามันทำงานยังไง'
        aboutText3.value = 'เมื่อผมเริ่มศึกษาหาความรู้เกี่ยวกับโปรแกรมมิ่ง ผมก็เริ่มเข้าใจว่ามันคือกระบวนการที่ทำให้โปรแกรมทำตามคำสั่งของผู้ใช้ ความสงสัยในตอนนั้นได้กลายเป็นความหลงใหลในการเขียนโปรแกรมจนถึงวันนี้'
        aboutText4.value = 'ตอนนี้ผมเรียนอยู่ที่ โรงเรียนทวีธาภิเษก, บางขุนเทียน และมีความสนใจในสาขาต่างๆ เช่น:'
        interest1.value = 'การพัฒนาเกม (Game Development)'
        interest2.value = 'การพัฒนาเว็บไซต์แบบ Full Stack (Full Stack Development)'
        interest3.value = 'ปัญญาประดิษฐ์ / การเรียนรู้ของเครื่อง (AI / Machine Learning)'
        interest4.value = 'การตัดต่อภาพและวิดีโอ (Photo / Video Editing)'
        buttonText.value = 'คลิกปุ่มเพื่อเปลี่ยนภาษา'
        buttonLabel.value = 'คลิกปุ่มเพื่อเปลี่ยนภาษา: ' 
    }
}
</script>

<style scoped>
.about-card {
    animation: fadeIn 1s ease-in-out, pulse 2s infinite;
    background: linear-gradient(135deg, rgba(255,255,255,0.9) 0%, rgba(255,255,255,0.7) 100%);
    border: 1px solid rgba(255,255,255,0.3);
    backdrop-filter: blur(10px);
    max-width: 100%;
    margin: 0 auto;
    padding: 1rem;
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(-20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes pulse {
    0%, 100% {
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    50% {
        box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
    }
}

@keyframes gradient {
    0% {
        background-position: 0% 50%;
    }
    50% {
        background-position: 100% 50%;
    }
    100% {
        background-position: 0% 50%;
    }
}

.animate-gradient {
    background-size: 200% 200%;
    animation: gradient 3s ease infinite;
}

img {
    transition: box-shadow 0.5s, transform 0.5s;
}

img:hover {
    transform: scale(1.1);
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
}

button {
    animation: bounce 2s infinite;
    background: linear-gradient(135deg, rgba(0,0,255,0.7) 0%, rgba(255,0,255,0.7) 100%);
    border: 1px solid rgba(255,255,255,0.3);
    backdrop-filter: blur(10px);
}

@keyframes bounce {
    0%, 100% {
        transform: translateY(0);
    }
    50% {
        transform: translateY(-10px);
    }
}

.tech-logo {
    width: 3rem;
    height: 3rem;
    margin: 0.5rem;
    border: 2px solid #93c5fd;
    border-radius: 9999px;
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
    transition: box-shadow 0.5s, transform 0.5s;
}

.tech-logo:hover {
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
    transform: scale(1.1);
}

@media (min-width: 768px) {
    .about-card {
        padding: 2rem;
    }
}

@media (min-width: 1024px) {
    .about-card {
        padding: 3rem;
    }
}
</style>
