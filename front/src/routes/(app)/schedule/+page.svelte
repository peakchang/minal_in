<script>
    import FullCalendar from "svelte-fullcalendar";
    import daygridPlugin from "@fullcalendar/daygrid";

    let options = {
        dateClick: (event) => alert("date click! " + event.dateStr),
        events: [
            { title: "09:00~12:00 김예지님", date: "2024-09-30" },
            { title: "event 2", date: "2024-09-30" },
            { title: "event 3", date: "2024-09-30" },
        ],
        initialView: "dayGridMonth",
        plugins: [daygridPlugin],
    };

    
</script>

<!-- <svelte:window on:load={() => console.log('DOM loaded')}> -->

<div class="max-w-[1000px] mx-auto px-2 pt-28">
    <FullCalendar {options} />
    <div class="text-center text-lg font-semibold">예약현황 페이지</div>

    <div class="text-sm">
        <p>☆ full calender API 사용해서 예약 현황 체크 할수 있게 하기</p>
        <p>☆ 예약 체크 및 하는것들 자동화 시키는 일단 만들어보고 조율조율!!!</p>
    </div>
</div>
