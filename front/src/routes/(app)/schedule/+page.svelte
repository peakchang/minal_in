<script>
    import FullCalendar from "svelte-fullcalendar";
    import daygridPlugin from "@fullcalendar/daygrid";
    // import ko from '@fullcalendar/core/locales/ko';
    import { browser } from "$app/environment";
    import { onMount } from "svelte";

    let options = {
        dateClick: (event) => alert("date click! " + event.dateStr),
        events: [
            { title: `09:00~12:00 김예지님`, date: "2024-11-30" },
            { title: `13:00~17:00 강다연님`, date: "2024-11-30" },
            { title: `19:00~ 오연주님`, date: "2024-11-30" },
            { title: "23:00~ 김승이님", date: "2024-11-08" },
            { title: "18:00~23:00 김미영님", date: "2024-11-15" },
        ],
        initialView: "dayGridMonth",
        plugins: [daygridPlugin],
        locale: "ko",
    };

    onMount(() => {
        if (browser) {
            const eventWrappers = document.querySelectorAll(".fc-sticky");


            eventWrappers.forEach((wrapper) => {
                // 엘리먼트 내의 텍스트를 가져옵니다.
                const textContent = wrapper.textContent.trim();

                // 텍스트를 공란 기준으로 나눕니다.
                const textArray = textContent.split(/\s+/);

                // 배열의 길이가 2 이상인지 확인합니다.
                if (textArray.length >= 2) {
                    // 상위 엘리먼트를 가져옵니다.
                    const parent = wrapper.parentElement;

                    // 기존 엘리먼트를 제거합니다.
                    parent.removeChild(wrapper);

                    parent.style.textAlign = "center";

                    // 첫 번째와 두 번째 텍스트를 사용하여 새로운 엘리먼트를 생성합니다.
                    const newWrapper1 = document.createElement("div");
                    const newWrapper2 = document.createElement("div");

                    // 각각의 새로운 엘리먼트에 텍스트를 추가합니다.
                    newWrapper1.textContent = textArray[0];
                    newWrapper2.textContent = textArray[1];

                    // 원한다면 클래스 추가
                    newWrapper1.classList.add("fc-sticky");
                    newWrapper2.classList.add("fc-sticky");

                    // 상위 엘리먼트에 새로운 엘리먼트들을 추가합니다.
                    parent.appendChild(newWrapper1);
                    parent.appendChild(newWrapper2);
                }
            });
        }
    });
</script>

<!-- <svelte:window on:load={() => console.log('DOM loaded')}> -->

<div class="max-w-[1000px] mx-auto px-2 pt-28">
    <div class="text-center text-lg font-semibold">예약현황 페이지</div>

    <div class="text-xs md:text-sm">
        <FullCalendar {options} />
    </div>

    <div class="text-sm">
        <p>☆ 예약 체크 및 하는것들 자동화 시키는 일단 만들어보고 조율조율!!!</p>
    </div>
</div>


