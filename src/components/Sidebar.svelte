<!-- src/Sidebar.svelte -->
<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    export let isOpen = true;
    export let isDark = false;

    if (window.matchMedia("(max-width: 1025px)").matches) {
        isOpen = false
    } else {
        isOpen = true
    }

    function toggleSidebar() {
        isOpen = !isOpen;
        dispatch("sidebarChange", { isOpen });
    }

    function toggleTheme() {
        document.documentElement.setAttribute(
            "data-theme",
            isDark ? "light" : "dark",
        );
        isDark = !isDark;
    }
</script>

<div class="sidebar {isOpen ? 'open' : 'close'}">
    <div class="top-bar">
        <div class="logo-cont top-line">
            <svg
                width="154"
                height="25"
                viewBox="0 0 154 25"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
            >
                <path
                    d="M151.528 21.892V8.31999H152.828V21.892H151.528ZM152.178 5.01799C151.884 5.01799 151.632 4.91399 151.424 4.70599C151.216 4.49799 151.112 4.25532 151.112 3.97799C151.112 3.68332 151.216 3.43199 151.424 3.22399C151.632 3.01599 151.884 2.91199 152.178 2.91199C152.49 2.91199 152.742 3.01599 152.932 3.22399C153.14 3.41465 153.244 3.65732 153.244 3.95199C153.244 4.24665 153.14 4.49799 152.932 4.70599C152.742 4.91399 152.49 5.01799 152.178 5.01799Z"
                    fill="var(--text-color)"
                />
                <path
                    d="M141.224 21.892L135.114 8.32001H136.492L142.212 21.164H141.588L147.36 8.32001H148.686L142.55 21.892H141.224Z"
                    fill="var(--text-color)"
                />
                <path
                    d="M127.182 8.21601C128.291 8.21601 129.253 8.43267 130.068 8.86601C130.9 9.28201 131.541 9.92334 131.992 10.79C132.46 11.6393 132.694 12.6967 132.694 13.962V21.892H131.394V14.066C131.394 12.5407 131.004 11.3793 130.224 10.582C129.461 9.78467 128.387 9.38601 127 9.38601C125.943 9.38601 125.024 9.60267 124.244 10.036C123.464 10.4693 122.866 11.076 122.45 11.856C122.051 12.636 121.852 13.572 121.852 14.664V21.892H120.552V2.60001H121.852V12.09L121.618 11.674C122.034 10.5993 122.719 9.75867 123.672 9.15201C124.625 8.52801 125.795 8.21601 127.182 8.21601Z"
                    fill="var(--text-color)"
                />
                <path
                    d="M109.733 21.996C108.433 21.996 107.271 21.7013 106.249 21.112C105.243 20.5227 104.437 19.708 103.831 18.668C103.241 17.628 102.947 16.4407 102.947 15.106C102.947 13.754 103.241 12.5667 103.831 11.544C104.437 10.504 105.243 9.68933 106.249 9.1C107.271 8.51066 108.433 8.216 109.733 8.216C111.033 8.216 112.194 8.51066 113.217 9.1C114.239 9.68933 115.045 10.504 115.635 11.544C116.224 12.5667 116.519 13.754 116.519 15.106C116.519 16.4407 116.224 17.628 115.635 18.668C115.045 19.708 114.239 20.5227 113.217 21.112C112.194 21.7013 111.033 21.996 109.733 21.996ZM109.733 20.826C110.773 20.826 111.709 20.592 112.541 20.124C113.373 19.6387 114.023 18.9627 114.491 18.096C114.959 17.2293 115.193 16.2327 115.193 15.106C115.193 13.962 114.959 12.9653 114.491 12.116C114.023 11.2493 113.373 10.582 112.541 10.114C111.709 9.62867 110.773 9.386 109.733 9.386C108.693 9.386 107.757 9.62867 106.925 10.114C106.11 10.582 105.46 11.2493 104.975 12.116C104.507 12.9653 104.273 13.962 104.273 15.106C104.273 16.2327 104.507 17.2293 104.975 18.096C105.46 18.9627 106.11 19.6387 106.925 20.124C107.757 20.592 108.693 20.826 109.733 20.826ZM111.449 5.902C111.067 5.902 110.721 5.81533 110.409 5.642C110.114 5.45133 109.845 5.24333 109.603 5.018C109.36 4.77533 109.117 4.56733 108.875 4.394C108.632 4.20333 108.372 4.108 108.095 4.108C107.696 4.108 107.375 4.264 107.133 4.576C106.89 4.87067 106.751 5.278 106.717 5.798H105.859C105.893 5.018 106.101 4.394 106.483 3.926C106.881 3.44066 107.393 3.198 108.017 3.198C108.398 3.198 108.736 3.29333 109.031 3.484C109.343 3.65733 109.62 3.86533 109.863 4.108C110.123 4.33333 110.365 4.54133 110.591 4.732C110.833 4.90533 111.093 4.992 111.371 4.992C111.769 4.992 112.09 4.84466 112.333 4.55C112.593 4.238 112.731 3.83933 112.749 3.354H113.607C113.589 4.09933 113.381 4.71467 112.983 5.2C112.584 5.668 112.073 5.902 111.449 5.902Z"
                    fill="var(--text-color)"
                />
                <path
                    d="M93.7113 22.022C92.7233 22.022 91.796 21.7967 90.9293 21.346C90.08 20.878 89.3953 20.2367 88.8753 19.422L89.6813 18.538C90.184 19.2834 90.7733 19.8554 91.4493 20.254C92.1426 20.6353 92.8966 20.826 93.7113 20.826C96.1206 20.826 97.3253 19.396 97.3253 16.536V4.88802H90.6173V3.69202H98.6513V16.536C98.6513 18.356 98.2353 19.7254 97.4033 20.644C96.5713 21.5627 95.3406 22.022 93.7113 22.022Z"
                    fill="var(--text-color)"
                />
                <path
                    d="M70.4984 24.492L79.0784 0H82.6924L74.1124 24.492H70.4984Z"
                    fill="var(--text-color)"
                />
                <path
                    d="M47.4078 14.638C47.4078 13.182 47.6938 11.8907 48.2658 10.764C48.8551 9.63734 49.6524 8.77067 50.6578 8.16401C51.6631 7.55734 52.7811 7.25401 54.0118 7.25401C54.9478 7.25401 55.8404 7.46201 56.6898 7.87801C57.5391 8.27667 58.2151 8.81401 58.7178 9.49001V2.65201H62.4098V21.892H58.7178V19.76C58.2671 20.4707 57.6344 21.0427 56.8198 21.476C56.0051 21.9093 55.0604 22.126 53.9858 22.126C52.7724 22.126 51.6631 21.814 50.6578 21.19C49.6524 20.566 48.8551 19.6907 48.2658 18.564C47.6938 17.42 47.4078 16.1113 47.4078 14.638ZM58.7438 14.69C58.7438 13.806 58.5704 13.052 58.2238 12.428C57.8771 11.7867 57.4091 11.3013 56.8198 10.972C56.2304 10.6253 55.5978 10.452 54.9218 10.452C54.2458 10.452 53.6218 10.6167 53.0498 10.946C52.4778 11.2753 52.0098 11.7607 51.6458 12.402C51.2991 13.026 51.1258 13.7713 51.1258 14.638C51.1258 15.5047 51.2991 16.2673 51.6458 16.926C52.0098 17.5673 52.4778 18.0613 53.0498 18.408C53.6391 18.7547 54.2631 18.928 54.9218 18.928C55.5978 18.928 56.2304 18.7633 56.8198 18.434C57.4091 18.0873 57.8771 17.602 58.2238 16.978C58.5704 16.3367 58.7438 15.574 58.7438 14.69Z"
                    fill="var(--text-color)"
                />
                <path
                    d="M38.1597 22.126C36.773 22.126 35.525 21.8227 34.4157 21.216C33.3063 20.592 32.431 19.7167 31.7897 18.59C31.1657 17.4633 30.8537 16.1633 30.8537 14.69C30.8537 13.2167 31.1743 11.9167 31.8157 10.79C32.4743 9.66333 33.367 8.79666 34.4937 8.19C35.6203 7.566 36.877 7.254 38.2637 7.254C39.6503 7.254 40.907 7.566 42.0337 8.19C43.1603 8.79666 44.0443 9.66333 44.6857 10.79C45.3443 11.9167 45.6737 13.2167 45.6737 14.69C45.6737 16.1633 45.3357 17.4633 44.6597 18.59C44.001 19.7167 43.0997 20.592 41.9557 21.216C40.829 21.8227 39.5637 22.126 38.1597 22.126ZM38.1597 18.954C38.8183 18.954 39.4337 18.798 40.0057 18.486C40.595 18.1567 41.063 17.6713 41.4097 17.03C41.7563 16.3887 41.9297 15.6087 41.9297 14.69C41.9297 13.3207 41.5657 12.272 40.8377 11.544C40.127 10.7987 39.2517 10.426 38.2117 10.426C37.1717 10.426 36.2963 10.7987 35.5857 11.544C34.8923 12.272 34.5457 13.3207 34.5457 14.69C34.5457 16.0593 34.8837 17.1167 35.5597 17.862C36.253 18.59 37.1197 18.954 38.1597 18.954Z"
                    fill="var(--text-color)"
                />
                <path
                    d="M21.5796 22.126C20.1929 22.126 18.9449 21.8227 17.8356 21.216C16.7263 20.592 15.8509 19.7167 15.2096 18.59C14.5856 17.4633 14.2736 16.1633 14.2736 14.69C14.2736 13.2167 14.5943 11.9167 15.2356 10.79C15.8943 9.66333 16.7869 8.79666 17.9136 8.19C19.0403 7.566 20.2969 7.254 21.6836 7.254C23.0703 7.254 24.3269 7.566 25.4536 8.19C26.5803 8.79666 27.4643 9.66333 28.1056 10.79C28.7643 11.9167 29.0936 13.2167 29.0936 14.69C29.0936 16.1633 28.7556 17.4633 28.0796 18.59C27.4209 19.7167 26.5196 20.592 25.3756 21.216C24.2489 21.8227 22.9836 22.126 21.5796 22.126ZM21.5796 18.954C22.2383 18.954 22.8536 18.798 23.4256 18.486C24.0149 18.1567 24.4829 17.6713 24.8296 17.03C25.1763 16.3887 25.3496 15.6087 25.3496 14.69C25.3496 13.3207 24.9856 12.272 24.2576 11.544C23.5469 10.7987 22.6716 10.426 21.6316 10.426C20.5916 10.426 19.7163 10.7987 19.0056 11.544C18.3123 12.272 17.9656 13.3207 17.9656 14.69C17.9656 16.0593 18.3036 17.1167 18.9796 17.862C19.6729 18.59 20.5396 18.954 21.5796 18.954Z"
                    fill="var(--text-color)"
                />
                <path
                    d="M8.528 21.892L3.64 15.756V21.892H0V2.65201H3.64V13.598L8.476 7.48801H13.208L6.864 14.716L13.26 21.892H8.528Z"
                    fill="var(--text-color)"
                />
            </svg>
            <button class="icon-btn close-btn" on:click={toggleSidebar}>
                <svg
                    width="40"
                    height="40"
                    viewBox="0 0 40 40"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                >
                    <circle
                        cx="20"
                        cy="20"
                        r="19"
                        fill="var(--bg-color-2)"
                        stroke="#9DA0A7"
                        stroke-width="2"
                    />
                    <line
                        x1="15"
                        y1="24.5858"
                        x2="24.5858"
                        y2="15"
                        stroke="var(--text-color)"
                        stroke-width="2"
                        stroke-linecap="round"
                    />
                    <line
                        x1="15.4142"
                        y1="15"
                        x2="25"
                        y2="24.5858"
                        stroke="var(--text-color)"
                        stroke-width="2"
                        stroke-linecap="round"
                    />
                </svg>
            </button>
        </div>
        <nav class="nav-btns">
            <!-- svelte-ignore a11y-invalid-attribute -->
            <a class="nav-btn" href="#">
                <div class="svg-wrap">
                    <svg
                        width="22"
                        height="22"
                        viewBox="0 0 22 22"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M7.5 21.5C7.5 19.1667 7.5 14.3 7.5 13.5C7.5 12.5 8 12 9 12C10 12 12 12 13 12C14 12 14.5 12.5 14.5 13.5C14.5 14.3 14.5 18.5 14.5 21"
                            stroke="#9DA0A7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M0.5 10.5H2.5V19C2.5 20.5 3.5 21.5 5 21.5H17C18.5 21.5 19.5 20.5 19.5 19V10.5H21L11 0.5L0.5 10.5Z"
                            stroke="#9DA0A7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                    </svg>
                </div>
                <span>Dashboard</span>
            </a>
            <!-- svelte-ignore a11y-invalid-attribute -->
            <a class="nav-btn" href="#">
                <div class="svg-wrap">
                    <svg
                        width="22"
                        height="22"
                        viewBox="0 0 22 22"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M5.5 6L0.5 11L5.5 16"
                            stroke="#9DA0A7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M16 16L21 11L16 6"
                            stroke="#9DA0A7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M13.5 1L8 21"
                            stroke="#9DA0A7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                    </svg>
                </div>
                <span>Study</span>
            </a>
            <a class="nav-btn selected" href="/">
                <div class="svg-wrap">
                    <svg
                        width="23"
                        height="23"
                        viewBox="0 0 23 23"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M1 1V22.5H22.5"
                            stroke="#9DA0A7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <circle cx="7.5" cy="9" r="2.5" stroke="#9DA0A7" />
                        <path d="M9.5 11L11.5 13" stroke="#9DA0A7" />
                        <path d="M18.5 8L15.5 13" stroke="#9DA0A7" />
                        <circle cx="13.5" cy="15" r="2.5" stroke="#9DA0A7" />
                        <circle cx="19.5" cy="6" r="2.5" stroke="#9DA0A7" />
                    </svg>
                </div>
                <span>Progress Tracker</span>
            </a>
            <!-- svelte-ignore a11y-invalid-attribute -->
            <a class="nav-btn" href="#">
                <div class="svg-wrap">
                    <svg
                        width="21"
                        height="26"
                        viewBox="0 0 21 26"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M1 5.99997C1 3.99997 3.5 3.49997 5 3.49997C8 3.49997 10.5 6.99997 10.5 6.99997C10.5 6.99997 13 3.49997 16.5 3.49997C18 3.49997 20.5 4.49997 20.5 5.99997"
                            stroke="#9DA0A7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M20.5 5.99997V25.5H11.5C6 25.5 1 17.5 1 12.5V5.99997C1 1.49997 4.5 0.499969 6.5 0.499969H14.5C17.5 0.499969 20.5 2.99997 20.5 5.99997Z"
                            stroke="#9DA0A7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M1 8.99997C1 11.5 3 17 10.5 17C18 17 20.5 11.5 20.5 8.99997"
                            stroke="#9DA0A7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M20.5 25.5C18.6667 25.3334 15 23.6 15 18C15 16 15 16 15 16"
                            stroke="#9DA0A7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <circle cx="5.5" cy="7.99997" r="2" fill="#9DA0A7" />
                        <circle cx="16.5" cy="7.99997" r="2" fill="#9DA0A7" />
                    </svg>
                </div>
                <span>Invitations</span>
            </a>
            <!-- svelte-ignore a11y-invalid-attribute -->
            <a class="nav-btn" href="#">
                <div class="svg-wrap">
                    <svg
                        width="19"
                        height="22"
                        viewBox="0 0 19 22"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M5.75 13L8.25 15.5L13.25 11"
                            stroke="#9DA0A7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <rect
                            x="6.25"
                            y="0.5"
                            width="7"
                            height="4"
                            rx="1.5"
                            stroke="#9DA0A7"
                        />
                        <path
                            fill-rule="evenodd"
                            clip-rule="evenodd"
                            d="M5.75 2H2.75C1.64543 2 0.75 2.89543 0.75 4V20C0.75 21.1046 1.64543 22 2.75 22H16.75C17.8546 22 18.75 21.1046 18.75 20V4C18.75 2.89543 17.8546 2 16.75 2H13.75V3L16.75 3C17.3023 3 17.75 3.44772 17.75 4V20C17.75 20.5523 17.3023 21 16.75 21H2.75C2.19772 21 1.75 20.5523 1.75 20V4C1.75 3.44772 2.19772 3 2.75 3H5.75V2Z"
                            fill="#9DA0A7"
                        />
                    </svg>
                </div>
                <span>Reviews</span>
            </a>
            <!-- svelte-ignore a11y-invalid-attribute -->
            <a class="nav-btn" href="#">
                <div class="svg-wrap">
                    <svg
                        width="22"
                        height="24"
                        viewBox="0 0 22 24"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M15.1419 15.2214C15.5622 14.1339 15.7724 13.5902 16.1138 13.5149C16.2036 13.495 16.2964 13.495 16.3862 13.5149C16.7276 13.5902 16.9378 14.1339 17.3581 15.2214C17.5971 15.8398 17.7166 16.149 17.9403 16.3593C18.003 16.4183 18.0711 16.4708 18.1436 16.5162C18.4021 16.6778 18.7247 16.7078 19.37 16.7678C20.4625 16.8693 21.0087 16.9201 21.1755 17.2433C21.21 17.3102 21.2335 17.3827 21.245 17.4577C21.3003 17.8198 20.8987 18.1989 20.0956 18.9572L19.8726 19.1677C19.4972 19.5222 19.3094 19.6995 19.2008 19.9207C19.1357 20.0534 19.092 20.1963 19.0716 20.3437C19.0374 20.5894 19.0924 20.8465 19.2024 21.3608L19.2416 21.5445C19.4388 22.4668 19.5374 22.9279 19.4143 23.1545C19.3038 23.3581 19.1002 23.4885 18.8752 23.4996C18.6248 23.512 18.272 23.2137 17.5663 22.6169C17.1014 22.2238 16.8689 22.0272 16.6109 21.9504C16.375 21.8802 16.125 21.8802 15.8891 21.9504C15.6311 22.0272 15.3986 22.2238 14.9337 22.6169C14.228 23.2137 13.8752 23.512 13.6248 23.4996C13.3998 23.4885 13.1962 23.3581 13.0857 23.1545C12.9626 22.9279 13.0612 22.4668 13.2584 21.5445L13.2976 21.3608C13.4076 20.8465 13.4626 20.5894 13.4284 20.3437C13.408 20.1963 13.3643 20.0534 13.2992 19.9207C13.1906 19.6995 13.0028 19.5222 12.6274 19.1677L12.4044 18.9572C11.6013 18.1989 11.1997 17.8198 11.255 17.4577C11.2665 17.3827 11.29 17.3102 11.3245 17.2433C11.4913 16.9201 12.0375 16.8693 13.13 16.7678C13.7753 16.7078 14.0979 16.6778 14.3564 16.5162C14.4289 16.4708 14.497 16.4183 14.5597 16.3593C14.7834 16.149 14.9029 15.8398 15.1419 15.2214Z"
                            stroke="#9DA0A7"
                        />
                        <path
                            fill-rule="evenodd"
                            clip-rule="evenodd"
                            d="M2.25 1.5H16.25C16.8023 1.5 17.25 1.94772 17.25 2.5V9.5H18.25V2.5C18.25 1.39543 17.3546 0.5 16.25 0.5H2.25C1.14543 0.5 0.25 1.39543 0.25 2.5V20.5C0.25 21.6046 1.14543 22.5 2.25 22.5H8.25V21.5H2.25C1.69772 21.5 1.25 21.0523 1.25 20.5V2.5C1.25 1.94772 1.69771 1.5 2.25 1.5Z"
                            fill="#9DA0A7"
                        />
                    </svg>
                </div>
                <span>Feedbacks</span>
            </a>
        </nav>
    </div>
    <div class="pd05">
        <button
            class="nav-btn theme-btn {isDark ? 'dark' : 'light'}"
            type="button"
            on:click={toggleTheme}
        >
            <div class="svg-wrap">
                {#if isDark}
                    <svg>
                        <svg
                            width="22"
                            height="22"
                            viewBox="0 0 22 22"
                            fill="none"
                            xmlns="http://www.w3.org/2000/svg"
                        >
                            <path
                                d="M17 2C17 2.26667 17 4.77778 17 6"
                                stroke="#0DFFD0"
                                stroke-linecap="round"
                                stroke-linejoin="round"
                            />
                            <path
                                d="M15 4H19"
                                stroke="#0DFFD0"
                                stroke-linecap="round"
                                stroke-linejoin="round"
                            />
                            <path
                                d="M20 9C20 9.13333 20 10.3889 20 11"
                                stroke="#0DFFD0"
                                stroke-linecap="round"
                                stroke-linejoin="round"
                            />
                            <path
                                d="M19 10H21"
                                stroke="#0DFFD0"
                                stroke-linecap="round"
                                stroke-linejoin="round"
                            />
                            <mask id="path-5-inside-1_86_472" fill="white">
                                <path
                                    fill-rule="evenodd"
                                    clip-rule="evenodd"
                                    d="M21.6007 13.9472C20.3848 14.6182 18.987 15 17.5 15C12.8056 15 9 11.1944 9 6.5C9 3.91603 10.153 1.60136 11.9726 0.0424081C11.6521 0.0143336 11.3277 0 11 0C4.92487 0 0 4.92487 0 11C0 17.0751 4.92487 22 11 22C16.0543 22 20.3124 18.5912 21.6007 13.9472Z"
                                />
                            </mask>
                            <path
                                d="M21.6007 13.9472L22.5643 14.2145C22.6719 13.8266 22.5365 13.412 22.2206 13.1625C21.9047 12.913 21.47 12.8772 21.1176 13.0717L21.6007 13.9472ZM11.9726 0.0424081L12.6232 0.801809C12.9289 0.539887 13.0478 0.120184 12.9248 -0.263136C12.8018 -0.646456 12.4609 -0.918642 12.0599 -0.953776L11.9726 0.0424081ZM21.1176 13.0717C20.0458 13.6631 18.8138 14 17.5 14V16C19.1602 16 20.7238 15.5733 22.0839 14.8227L21.1176 13.0717ZM17.5 14C13.3579 14 10 10.6421 10 6.5H8C8 11.7467 12.2533 16 17.5 16V14ZM10 6.5C10 4.22026 11.0159 2.17888 12.6232 0.801809L11.322 -0.716993C9.2901 1.02383 8 3.61179 8 6.5H10ZM11 1C11.2986 1 11.5939 1.01306 11.8853 1.03859L12.0599 -0.953776C11.7104 -0.98439 11.3569 -1 11 -1V1ZM1 11C1 5.47715 5.47715 1 11 1V-1C4.37258 -1 -1 4.37258 -1 11H1ZM11 21C5.47715 21 1 16.5228 1 11H-1C-1 17.6274 4.37258 23 11 23V21ZM20.6371 13.6799C19.4658 17.9022 15.5934 21 11 21V23C16.5152 23 21.159 19.2802 22.5643 14.2145L20.6371 13.6799Z"
                                fill="#0DFFD0"
                                mask="url(#path-5-inside-1_86_472)"
                            />
                        </svg>
                    </svg>
                {:else}
                    <svg
                        width="24"
                        height="24"
                        viewBox="0 0 24 24"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M21 12H23"
                            stroke="#C7D100"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M18 6L20 4"
                            stroke="#C7D100"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M6 6L4 4"
                            stroke="#C7D100"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M3 12H1"
                            stroke="#C7D100"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M6 18L4 20"
                            stroke="#C7D100"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M12 21V23"
                            stroke="#C7D100"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M18 18L20 20"
                            stroke="#C7D100"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M12 3V1"
                            stroke="#C7D100"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <circle cx="12" cy="12" r="5.5" stroke="#C7D100" />
                    </svg>
                {/if}
            </div>
            <span
                >{#if isDark}Dark{:else}Light{/if}</span
            >
        </button>
    </div>
    <div class="bottom-nav-btns">
        <!-- svelte-ignore a11y-invalid-attribute -->
        <a class="nav-btn" href="#">
            <div class="svg-wrap">
                <svg
                    width="22"
                    height="22"
                    viewBox="0 0 22 22"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                >
                    <circle cx="11" cy="11" r="10.5" stroke="#9DA0A7" />
                    <circle cx="11" cy="9" r="3.5" stroke="#9DA0A7" />
                    <path
                        fill-rule="evenodd"
                        clip-rule="evenodd"
                        d="M3.1306 18.6859C3.81173 16.5892 7.07593 15 11 15C14.9241 15 18.1883 16.5892 18.8694 18.6859C18.5942 18.9676 18.3039 19.2347 17.9999 19.4857C17.993 18.7678 17.4614 17.9179 16.1666 17.1896C14.8946 16.4741 13.0699 16 11 16C8.93009 16 7.10545 16.4741 5.83342 17.1896C4.53862 17.9179 4.00703 18.7678 4.00008 19.4857C3.69611 19.2347 3.40585 18.9676 3.1306 18.6859Z"
                        fill="#9DA0A7"
                    />
                </svg>
            </div>
            <span>Kaur Kuslap</span>
        </a>
        <!-- svelte-ignore a11y-invalid-attribute -->
        <a class="nav-btn" href="#">
            <div class="svg-wrap">
                <svg
                    width="20"
                    height="20"
                    viewBox="0 0 20 20"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                >
                    <path
                        d="M10 10.5V0.5"
                        stroke="#9DA0A7"
                        stroke-linecap="square"
                        stroke-linejoin="round"
                    />
                    <path
                        fill-rule="evenodd"
                        clip-rule="evenodd"
                        d="M15.8824 2.68821C15.9595 2.30414 16 1.9068 16 1.5C16 1.49976 16 1.49951 16 1.49927C18.4289 3.32368 20 6.22836 20 9.5C20 15.0228 15.5228 19.5 10 19.5C4.47715 19.5 0 15.0228 0 9.5C0 6.22836 1.57111 3.32368 4 1.49927C4 1.49951 4 1.49976 4 1.5C4 1.9068 4.04048 2.30414 4.11764 2.68821C2.20824 4.33855 1 6.77817 1 9.5C1 14.4706 5.02944 18.5 10 18.5C14.9706 18.5 19 14.4706 19 9.5C19 6.77817 17.7918 4.33855 15.8824 2.68821Z"
                        fill="#9DA0A7"
                    />
                </svg>
            </div>
            <span>Log out</span>
        </a>
    </div>
</div>

<style>
    .sidebar {
        position: fixed;
        top: 0;
        left: 0;
        width: 14rem;
        height: 100vh;

        display: flex;
        flex-direction: column;
        flex: 1 1 0%;
        border-right: 1px solid var(--stroke);
        background-color: var(--menu-color);

        transition: transform 0.3s ease;
    }

    .sidebar.open {
        transform: translateX(0);
    }

    .sidebar.close {
        transform: translateX(-100%);
    }

    .logo-cont {
        padding: 0 1rem;
    }

    .top-bar {
        flex: 1 1 0%;
        padding-top: 1.25rem;
    }

    .svg-wrap {
        position: relative;
        height: 1.75rem;
        width: 1.75rem;
    }

    .svg-wrap svg {
        height: 1.5rem;
        width: 1.5rem;
    }

    a {
        text-decoration: none;
    }

    .nav-btn {
        display: flex;
        flex-direction: row;
        align-items: center;
        gap: 0.5rem;
        padding: 0.5rem;
        border-radius: 0.375rem;
    }

    .nav-btn:hover {
        background-color: var(--btn-hovered);
        color: var(--text-color);
    }

    .selected {
        background-color: var(--btn-active);
        color: var(--text-color);
        pointer-events: none;
    }

    .selected svg path {
        stroke: var(--accent);
    }

    .selected svg circle {
        stroke: var(--accent);
    }

    .selected svg rect {
        stroke: var(--accent);
    }

    .nav-btns {
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
        padding: 0 0.5rem;
        margin-top: 1.25rem;
        flex: 1 1 0%;
    }

    .theme-btn {
        border-style: none;
        width: 100%;
        margin: 0;
        background-color: transparent;
        color: var(--gray-text-color);
        font-family: var(--body-font-family);
        font-size: var(--body-font-size);
        font-weight: var(--body-font-weight);
    }

    .bottom-nav-btns {
        padding: 0.5rem;
        --tw-border-opacity: 1;
        border-top-width: 1px;
        flex-direction: column;
        flex-shrink: 0;
        display: flex;
        gap: 0.5rem;
        border-top: 1px solid var(--stroke);
    }

    .top-line {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
    }

    .close-btn {
        display: none;
    }

    @media (max-width: 1025px) {
        .sidebar {
            transform: translateX(-100%);
            width: 100%;
            border-width: 0;
        }

        .top-bar {
            padding-top: 0.75rem;
        }
        
        .close-btn {
            display: block;
        }
    }
</style>
