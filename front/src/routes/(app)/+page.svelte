<script>
    import { browser } from "$app/environment";
    import { onMount } from "svelte";
    let swiper;
    let imgArr = [
        "img1.jpeg",
        "img2.jpeg",
        "img3.jpeg",
        "img4.jpeg",
        "img5.jpeg",
        "img6.jpeg",
        "img7.jpeg",
        "img8.jpeg",
    ];

    let imgHeights = [];
    // let windowHeight = window.innerHeight;
    let windowHeight = 0;
    let wrapperHeights = [];

    onMount(() => {
        // init Swiper:
        swiper = new Swiper(".main-swiper", {
            loop: true,
            effect: "fade",
            spaceBetween: 30,
            autoplay: {
                delay: 3000,
            },
        });

        const imgs = document.querySelectorAll("img");
        console.log(imgs);

        imgs.forEach((img, index) => {
            img.onload = () => {
                const imgHeight = img.clientHeight;
                console.log(imgHeight);
                
                imgHeights[index] = imgHeight;
                adjustHeight(index, imgHeight);
            };
        });
    });

    function adjustHeight(index, imgHeight) {
        if (browser) {
            windowHeight = window.innerHeight;
            wrapperHeights[index] =
                imgHeight > windowHeight ? "100vh" : `${imgHeight}px`;
        }
    }
</script>

<div class="fixed top-0 left-0 w-full z-50"></div>
<div class="">
    <div class="main-swiper">
        <!-- Additional required wrapper -->
        <div class="swiper-wrapper">
            <!-- Slides -->
            {#each imgArr as img, idx}
                <div
                    class="swiper-slide img_wrapper"
                    style="height: {wrapperHeights[idx] || 'auto'}"
                >
                    <img src="/swiper_img/{img}" alt="" />
                </div>
            {/each}
        </div>
    </div>

    asdfasdfasdf
    <div class="bg-red-500">aslfjaisjdfliajsdf</div>
</div>

<style>
    .main-swiper {
        height: 100vh;
        border: 1px solid red;
        overflow: hidden;
    }
    .swiper-slide img {
        width: 100%;
        height: auto;
    }
</style>
