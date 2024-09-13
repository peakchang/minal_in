<script>
    let yAxis;
    let inner_width;
    let gnbWhiteBool = false;

    $: yAxis, senseYAxis();
    function senseYAxis() {
        if (yAxis > 70) {
            gnbWhiteBool = true;
        } else {
            gnbWhiteBool = false;
        }
    }

    const menuList = [
        { name: "오시는길", link: "location" },
        { name: "예약현황", link: "schedule" },
        { name: "예약하기", link: "reservation" },
        { name: "문의하기", link: "contact" },
    ];
</script>

<svelte:window bind:scrollY={yAxis} bind:innerWidth={inner_width} />

<div
    class="hidden md:block fixed left-0 top-0 z-[9999] w-full gnb-wrapper px-8 py-3"
    class:scrolled={gnbWhiteBool}
>
    <div class="flex justify-between items-center">
        <div class="w-60">
            <a href="/">
                <img src="/logo.png" alt="" class="w-full" />
            </a>
        </div>
        <div>
            <ul class="flex items-center gap-8 font-semibold text-lg">
                {#each menuList as menu}
                    <li><a href={menu.link}>{menu.name}</a></li>
                {/each}
            </ul>
        </div>
    </div>
</div>

<div
    class="md:hidden fixed left-0 top-0 z-[9999] w-full gnb-wrapper px-8 pt-3"
    class:scrolled={gnbWhiteBool}
>
    <div class=" w-32 mx-auto">
        <a href="/">
            <img src="/logo.png" alt="" class="w-full" />
        </a>
    </div>
    <div class="pt-1 pb-2">
        <ul class="flex justify-around text-sm">
            {#each menuList as menu}
                <li><a href={menu.link}>{menu.name}</a></li>
            {/each}
        </ul>
    </div>
</div>

<div>
    <slot></slot>
</div>

<hr class="my-3 border-none h-0.5 bg-gray-400" />

<div class="max-w-[1000px] mx-auto pt-3 pb-8">푸터푸터!!!</div>

<style>
    .gnb-wrapper {
        background-color: rgba(55, 65, 81, 0.25);
        transition: background-color 0.3s ease; /* 애니메이션 설정 */
        color: white;
    }
    .gnb-wrapper.scrolled {
        background-color: white; /* 스크롤 시 흰색으로 변경 */
        border-bottom: 2px solid black;
        color: black;
    }
</style>
