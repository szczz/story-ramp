<template>
    <div
        :class="isMenuOpen ? 'w-72' : ''"
        class="nav-bar sticky self-start w-12 duration-500 ease-in-out transition-width"
    >
        <div class="flex items-center mt-4 mb-12">
            <button
                class="flex items-center flex-shrink-0 px-2 py-1 mx-1 overflow-hidden"
                :aria-label="$t('chapters.menu')"
                :tabindex="isMenuOpen ? 0 : -1"
                @click="isMenuOpen = !isMenuOpen"
            >
                <svg
                    v-tippy="{
                        delay: 200,
                        placement: 'right',
                        content: $t('chapters.title'),
                        onShow: () => !isMenuOpen,
                        animateFill: true,
                        animation: 'chapter-menu'
                    }"
                    class="flex-shrink-0"
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    stroke="#707070"
                >
                    <path class="transition-all duration-500 ease-in-out" :d="`m3.5 7h${isMenuOpen ? '17' : '8.5'}`" />
                    <path class="transition-all duration-500 ease-in-out" :d="`m3.5 12h${isMenuOpen ? '17' : '8.5'}`" />
                    <path d="m3.5 17h17" />
                </svg>
                <span class="flex-1 ml-4 overflow-hidden leading-normal overflow-ellipsis whitespace-nowrap">{{
                    $t('chapters.title')
                }}</span>
            </button>
        </div>

        <ul class="nav-content menu">
            <li v-if="introExists && returnToTop">
                <span
                    class="flex items-center px-2 py-1 mx-1 cursor-pointer"
                    @click="scrollToChapter('intro')"
                    @keydown.enter="scrollToChapter('intro')"
                    v-tippy="{
                        delay: '200',
                        placement: 'right',
                        content: $t('chapters.return'),
                        animateFill: true,
                        animation: 'chapter-menu'
                    }"
                    tabindex="0"
                    v-if="plugin"
                    role="button"
                >
                    <svg
                        class="flex-shrink-0"
                        viewBox="0 0 24 24"
                        width="24px"
                        height="24px"
                        fill="#fff"
                        stroke="#878787"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            data-v-689fab2c=""
                            d="m19.325 16.229c-2.4415 1.4096-4.8829 2.8191-7.3244 4.2286-2.4415-1.4096-4.883-2.8192-7.3245-4.2288-3.55e-5 -2.8191-7.1e-5 -5.6383-1.066e-4 -8.4574 2.4415-1.4096 4.8829-2.8191 7.3244-4.2286 2.4415 1.4096 4.883 2.8192 7.3245 4.2288 3.7e-5 2.8191 7.4e-5 5.6383 1.1e-4 8.4574z"
                            stroke-width=".93974"
                            style="fill: rgba(255, 255, 255, 0); fill-opacity: 0"
                            transform="matrix(1, 0, 0, 1, 8.881784197001252e-16, 0)"
                        />
                        <g transform="matrix(1, 0, 0, 1, 0.07912001013755887, 1.1142139434814453)">
                            <polygon
                                points="11.956 9.662 9.522 12.097 9.862 12.437 11.956 10.344 14.049 12.437 14.39 12.097"
                                style=""
                            />
                            <path
                                style="fill: rgb(135, 135, 135); stroke-width: 1.5px"
                                d="M 11.917 10.545 L 11.917 15.649"
                            />
                        </g>
                        <rect
                            x="9.114"
                            y="8.74"
                            width="5.842"
                            height="0.487"
                            style=""
                            transform="matrix(1, 0, 0, 1, 8.881784197001252e-16, 0)"
                        />
                    </svg>
                    <span class="flex-1 ml-4 overflow-hidden leading-normal overflow-ellipsis whitespace-nowrap">{{
                        $t('chapters.return')
                    }}</span>
                </span>

                <router-link
                    :to="{ hash: '#intro' }"
                    class="flex items-center px-2 py-1 mx-1"
                    target
                    v-tippy="{
                        delay: '200',
                        placement: 'right',
                        content: $t('chapters.return'),
                        animateFill: true,
                        animation: 'chapter-menu'
                    }"
                    v-else
                >
                    <svg
                        class="flex-shrink-0"
                        viewBox="0 0 24 24"
                        width="24px"
                        height="24px"
                        fill="#fff"
                        stroke="#878787"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            data-v-689fab2c=""
                            d="m19.325 16.229c-2.4415 1.4096-4.8829 2.8191-7.3244 4.2286-2.4415-1.4096-4.883-2.8192-7.3245-4.2288-3.55e-5 -2.8191-7.1e-5 -5.6383-1.066e-4 -8.4574 2.4415-1.4096 4.8829-2.8191 7.3244-4.2286 2.4415 1.4096 4.883 2.8192 7.3245 4.2288 3.7e-5 2.8191 7.4e-5 5.6383 1.1e-4 8.4574z"
                            stroke-width=".93974"
                            style="fill: rgba(255, 255, 255, 0); fill-opacity: 0"
                            transform="matrix(1, 0, 0, 1, 8.881784197001252e-16, 0)"
                        />
                        <g transform="matrix(1, 0, 0, 1, 0.07912001013755887, 1.1142139434814453)">
                            <polygon
                                points="11.956 9.662 9.522 12.097 9.862 12.437 11.956 10.344 14.049 12.437 14.39 12.097"
                                style=""
                            />
                            <path
                                style="fill: rgb(135, 135, 135); stroke-width: 1.5px"
                                d="M 11.917 10.545 L 11.917 15.649"
                            />
                        </g>
                        <rect
                            x="9.114"
                            y="8.74"
                            width="5.842"
                            height="0.487"
                            style=""
                            transform="matrix(1, 0, 0, 1, 8.881784197001252e-16, 0)"
                        />
                    </svg>
                    <span class="flex-1 ml-4 overflow-hidden leading-normal overflow-ellipsis whitespace-nowrap">{{
                        $t('chapters.return')
                    }}</span>
                </router-link>
            </li>

            <!-- Build custom configured table of contents -->
            <template v-if="customToc">
                <li
                    v-for="(item, idx) in customToc"
                    :key="idx"
                    :class="{
                        'is-active': lastActiveIdx === item.slideIndex || isSublistActive(item.sublist)
                    }"
                >
                    <toc-item :tocItem="item" :slides="slides" :plugin="plugin" @scroll-to-slide="scrollToTarget">
                        <button
                            class="mr-1"
                            :aria-label="$t('chapters.menu.dropdown')"
                            v-if="item.sublist && item.sublist.length && isMenuOpen"
                            @click="toggleSublist(idx)"
                        >
                            <svg
                                data-v-b1261e08=""
                                xmlns="http://www.w3.org/2000/svg"
                                height="18"
                                viewBox="0 0 24 24"
                                width="18"
                                class="rotate-180"
                                v-if="isSublistToggled(idx)"
                            >
                                <path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"></path>
                            </svg>
                            <svg
                                data-v-b1261e08=""
                                xmlns="http://www.w3.org/2000/svg"
                                height="18"
                                viewBox="0 0 24 24"
                                width="18"
                                v-else
                            >
                                <path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"></path>
                            </svg>
                        </button>
                    </toc-item>

                    <!-- Dropdown for sublists -->
                    <ul v-show="isSublistToggled(idx)" class="sublist-menu">
                        <li
                            v-for="(subItem, subIdx) in item.sublist"
                            :key="subIdx"
                            :class="{
                                'is-active': lastActiveIdx === subItem.slideIndex
                            }"
                        >
                            <toc-item
                                :tocItem="subItem"
                                :slides="slides"
                                :parentItem="false"
                                :plugin="plugin"
                            ></toc-item>
                        </li>
                    </ul>
                </li>
            </template>

            <!-- Default table of contents -->
            <template v-else>
                <li
                    v-for="(slide, idx) in tocSlides"
                    :key="idx"
                    :class="{ 'is-active': lastActiveIdx === slide.index }"
                >
                    <toc-item
                        :tocItem="{ ...slide, slideIndex: slide.index }"
                        :slides="slides"
                        :plugin="plugin"
                        @scroll-to-slide="scrollToTarget"
                    ></toc-item>
                </li>
            </template>
        </ul>
    </div>
</template>

<script setup lang="ts">
import type { PropType } from 'vue';
import { computed, ref, watch, onMounted } from 'vue';
import type { MenuItem, Slide } from '@storylines/definitions';
import TocItem from '@storylines/components/panels/helpers/toc-item.vue';

const props = defineProps({
    returnToTop: {
        type: Boolean,
        default: true
    },
    slides: {
        type: Array as PropType<Array<Slide>>,
        required: true
    },
    customToc: {
        type: Array as PropType<Array<MenuItem>>,
        required: false
    },
    activeChapterIndex: {
        type: Number,
        required: true
    },
    lang: {
        type: String,
        required: true
    },
    plugin: {
        type: Boolean,
        default: false
    }
});

const isMenuOpen = ref(false);
const introExists = ref(false);
const lastActiveIdx = ref(-1);

const sublistToggled = ref({} as Record<number, boolean>);

const emit = defineEmits(['scroll-to-slide']);

// filter out which slides are visible in the table of contents while preserving original slide index
const tocSlides = computed(() => {
    let slides = props.slides.map((slide, idx) => ({ ...slide, index: idx }));
    if (!props.customToc) {
        slides = slides.filter((slide) => slide.includeInToc !== false);
    }
    return slides;
});

const scrollToTarget = (index) => {
    emit('scroll-to-slide', index);
};

const customTocSlides = computed(() => {
    if (props.customToc) {
        // for custom ToC extract slides including nested sublist items
        let slides: MenuItem[] = [];
        props.customToc.forEach((item) => {
            slides.push(item);
            if (item.sublist && item.sublist.length) {
                item.sublist.forEach((subItem) => {
                    slides.push(subItem);
                });
            }
        });
        return slides;
    }
});

watch(
    () => props.activeChapterIndex,
    () => {
        updateActiveIdx();
    }
);

onMounted(() => {
    const introSection = document.getElementById('intro');
    introExists.value = !!introSection;
    if (props.customToc) {
        props.customToc.forEach((item, idx) => {
            sublistToggled.value[idx] = false;
        });
    }
});

const scrollToChapter = (id: string): void => {
    const el = document.getElementById(id);
    if (el) {
        el.scrollIntoView({ behavior: 'smooth' });
    }
};

const toggleSublist = (index: number): void => {
    sublistToggled.value[index] = !sublistToggled.value[index];
};

const isSublistToggled = (index: number): boolean => {
    return sublistToggled.value[index];
};

const isSublistActive = (sublist: MenuItem[] | undefined): boolean => {
    if (sublist) {
        return sublist.some((subItem) => lastActiveIdx.value === subItem.slideIndex);
    }
    return false;
};

const updateActiveIdx = () => {
    if (props.customToc) {
        const prevCustomSlides: MenuItem[] = customTocSlides.value!.filter(
            (slide) => slide.slideIndex <= props.activeChapterIndex
        );
        lastActiveIdx.value = prevCustomSlides.length ? prevCustomSlides[prevCustomSlides.length - 1].slideIndex : -1;
    } else {
        const prevSlides = tocSlides.value.filter((slide) => slide.index <= props.activeChapterIndex);
        lastActiveIdx.value = prevSlides.length ? prevSlides[prevSlides.length - 1].index : -1;
    }
};
</script>

<style lang="scss" scoped>
.nav-bar {
    max-height: calc(100vh - 4rem);
    display: flex;
    flex-direction: column;
}

.nav-content {
    overflow-y: auto;
    -ms-overflow-style: none; /* Internet Explorer 10+ */
    scrollbar-width: none; /* Firefox */
}

.nav-content::-webkit-scrollbar {
    display: none; /* Safari and Chrome */
}

.menu > li {
    a:hover {
        text-decoration: none;
        color: inherit;
    }

    a:focus {
        text-decoration: none;
        color: inherit;
    }

    a:hover svg {
        stroke: var(--sr-accent-colour);
    }

    a:visited {
        color: inherit;
    }

    &.is-active {
        :deep(svg) {
            fill: var(--sr-accent-colour);
            stroke: var(--sr-accent-colour);
        }

        :deep(span) {
            font-weight: bold;
        }
    }
}

.sublist-menu {
    > li {
        font-weight: normal;
        :deep(svg) {
            fill: #fff !important;
            stroke: #878787 !important;
        }

        :deep(span) {
            font-weight: normal !important;
        }

        &.is-active {
            :deep(span) {
                font-weight: bold !important;
            }

            :deep(svg) {
                fill: var(--sr-accent-colour) !important;
                stroke: var(--sr-accent-colour) !important;
            }
        }
    }
}

.rotate-180 {
    transform: rotate(-180deg);
}
</style>
