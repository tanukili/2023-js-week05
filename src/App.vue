<script>
import PackageCard from './components/PackageCard.vue';

export default {
  components: {
    PackageCard,
  },
};
</script>

<template>
  <div class="container" style="padding-top: 120px; padding-bottom: 100px">
    <div class="row justify-content-center">
      <div class="col-10">
        <div class="shadow rounded-1" style="padding: 60px 0">
          <div class="row justify-content-center">
            <div class="col-5 w-40">
              <img src="/main_img.png" alt="主視覺" class="img-fluid" />
              <h1 class="logo mb-0">Let's Travel!</h1>
            </div>
            <div class="col-5 w-40">
              <div class="text-primary">
                <h2
                  class="border-bottom border-3 fs-4 fw-bold pb-1 d-flex align-items-center"
                >
                  <span class="material-symbols-outlined me-1">
                    add_circle </span
                  >新增旅遊套票
                </h2>
                <form action="#">
                  <div class="row align-items-center pt-3">
                    <div class="col-3">
                      <label
                        for="packageName"
                        class="col-form-label fw-medium text-primary"
                        >套票名稱</label
                      >
                    </div>
                    <div class="col-9">
                      <input
                        type="text"
                        id="packageName"
                        class="form-control border-bottom rounded-top-1"
                        placeholder="請填寫套票名稱"
                      />
                    </div>
                  </div>
                  <div class="row align-items-center pt-4">
                    <div class="col-3">
                      <label
                        for="packageUrl"
                        class="col-form-label fw-medium text-primary"
                        >圖片網址</label
                      >
                    </div>
                    <div class="col-9">
                      <input
                        type="url"
                        id="packageUrl"
                        class="form-control border-bottom rounded-top-1"
                        placeholder="請填寫圖片網址"
                      />
                    </div>
                  </div>
                  <div class="row align-items-center pt-4">
                    <div class="col-3">
                      <label
                        for="packArea"
                        class="col-form-label fw-medium text-primary"
                        >景點地區</label
                      >
                    </div>
                    <div class="col-9 select-icon position-relative">
                      <select
                        id="packArea"
                        class="form-select border-bottom rounded-top-1"
                      >
                        <option>請選擇景點地區</option>
                        <option value="taipei">台北</option>
                        <option value="taichung">台中</option>
                        <option value="kaohsiung">高雄</option>
                      </select>
                    </div>
                  </div>
                  <div class="row align-items-center pt-4">
                    <div class="col-3">
                      <label
                        for="packagePrice"
                        class="col-form-label fw-medium text-primary"
                        >套票金額</label
                      >
                    </div>
                    <div class="col-9">
                      <input
                        type="text"
                        id="packagePrice"
                        class="form-control border-bottom rounded-top-1"
                        placeholder="請填寫套票金額"
                      />
                    </div>
                  </div>
                  <div class="row align-items-center pt-4">
                    <div class="col-3">
                      <label
                        for="packageNum"
                        class="col-form-label fw-medium text-primary"
                        >套票組數</label
                      >
                    </div>
                    <div class="col-9">
                      <input
                        type="text"
                        id="packageNum"
                        class="form-control border-bottom rounded-top-1"
                        placeholder="請填寫套票組數"
                      />
                    </div>
                  </div>
                  <div class="row align-items-center pt-4">
                    <div class="col-3">
                      <label
                        for="packageStarts"
                        class="col-form-label fw-medium text-primary"
                        >套票星級</label
                      >
                    </div>
                    <div class="col-9">
                      <input
                        type="text"
                        id="packageStarts"
                        class="form-control border-bottom rounded-top-1"
                        placeholder="請填寫套票星級"
                      />
                    </div>
                  </div>
                  <div class="row pt-4">
                    <div class="col-3">
                      <label
                        for="packageDescribe"
                        class="col-form-label fw-medium text-primary"
                        >套票描述</label
                      >
                    </div>
                    <div class="col-9">
                      <input
                        type="text"
                        id="packageDescribe"
                        class="form-control border-bottom rounded-top-1"
                        style="padding-bottom: 89px"
                        placeholder="請填寫套票描述（限 100 字）"
                      />
                    </div>
                  </div>
                  <div class="row">
                    <div class="col-6 ms-auto">
                      <button
                        type="submit"
                        class="btn btn-primary fs-5 mt-4 w-100"
                      >
                        新增套票
                      </button>
                    </div>
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="bg-gray-200">
    <div class="container" style="padding-bottom: 120px">
      <div class="row align-items-center py-5 mb-2">
        <div class="col-4">
          <div class="row justify-content-end mt-1">
            <div class="col-9 select-icon position-relative">
              <select
                class="form-select bg-white border border-gray-500 rounded-1"
              >
                <option>地區搜尋</option>
                <option value="all">全部地區</option>
                <option value="taipei">台北</option>
                <option value="taichung">台中</option>
                <option value="kaohsiung">高雄</option>
              </select>
            </div>
          </div>
        </div>
        <div class="col-2">
          <span class="text-secondary">本次搜尋共 6 筆資料</span>
        </div>
      </div>
      <div class="row">
        <PackageCard />
      </div>
    </div>
  </div>
</template>

<style>
.btn-primary {
  --bs-btn-hover-bg: #004e4d;
}
.logo {
  background: url(/logo.png);
  width: 350px;
  height: 235px;
  display: block;
  text-indent: 101%;
  white-space: nowrap;
  overflow: hidden;
  background-size: cover;
  background-position: center;
}
.w-40 {
  width: 40% !important;
}
.select-icon::before,
.select-icon::after {
  content: '';
  position: absolute;
  border: 4px solid;
  right: 26px;
}
.select-icon::before {
  border-color: transparent transparent var(--bs-primary) transparent;
  top: 11px;
}
.select-icon::after {
  border-color: var(--bs-primary) transparent transparent transparent;
  bottom: 11px;
}
</style>
