<script setup>
defineProps({
  msg: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <div class="col-4">
    <div class="card shadow border-gray-300">
      <div class="position-relative">
        <img
          src="/travel_1.png"
          class="card-img-top img-fluid"
          alt="套票預覽"
          style="height: 180px"
        />
        <span
          class="badge position-absolute translate-middle-y start-0 bg-info fs-5 py-2"
          style="top: 5%"
        >
          台北
        </span>
        <span
          class="badge position-absolute translate-middle-y start-0 top-100 bg-primary px-2 lh-base"
        >
          8.6
        </span>
      </div>
      <div class="card-body pb-2">
        <h3 class="card-title fs-4 border-bottom border-2 pb-1">
          綠島自由行套裝行程
        </h3>
        <p class="card-text lh-lg">
          嚴選超高CP值綠島自由行套裝行程，多種綠島套裝組合，提供台東綠島來回船票、綠島環島機車、綠島民宿住宿，行程加贈『綠島浮潛體驗』以及『綠島生態導覽』，讓你用輕鬆的綠島套裝自由行，也能深度認識綠島在地文化。
        </p>
      </div>
      <div
        class="card-footer border-0 text-primary d-flex justify-content-between align-items-center"
      >
        <small class="d-flex align-items-center fs-6 fw-medium"
          ><span
            class="material-symbols-outlined fs-5 me-1"
            style="font-variation-settings: 'FILL' 1"
          >
            error </span
          >剩下最後 8 組</small
        >
        <p class="mb-0 fw-medium d-flex align-items-center">
          TWD<span class="fs-2 ms-1">$1,280</span>
        </p>
      </div>
    </div>
  </div>
</template>

<style>
.badge {
  line-height: 1.2;
}
option {
  appearance: none;
  -moz-appearance: none;
  -webkit-appearance: none;
  color: #212529;
}
</style>
