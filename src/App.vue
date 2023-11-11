<script>
export default {
  data() {
    return {
      data: [],
      newPackage: {
        id: null,
        name: '',
        imgUrl: '',
        area: '',
        description: '',
        group: null,
        price: null,
        rate: null,
      },
    };
  },
  methods: {
    // 渲染方法
    render(nowArea = '全部地區') {
      let cardsHtml = '';
      let renderData = [];
      // 新增地區判斷
      if (nowArea !== '全部地區') {
        renderData = this.data.filter((e) => e.area === nowArea);
      } else {
        renderData = this.data;
      }
      renderData.forEach((e) => {
        const template = `
        <div class="col-md-6 col-xl-4">
          <div class="card shadow border-gray-300 h-100"">
            <div class="position-relative">
              <img
                src="${e.imgUrl}"
                class="card-img-top img-fluid"
                alt="套票預覽${e.id}"
                style="height: 180px"
              />
              <span
                class="badge position-absolute translate-middle-y start-0 bg-info fs-5 py-2"
                style="top: 5%"
              >
                ${e.area}
              </span>
              <span
                class="badge position-absolute translate-middle-y start-0 top-100 bg-primary lh-base px-2"
                style="width: 40px"
              >
                ${e.rate}
              </span>
            </div>
            <div class="card-body pb-2">
              <h3 class="card-title fs-4 border-bottom border-2 pb-1">
                ${e.name}
              </h3>
              <p class="card-text lh-lg">
                ${e.description}
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
                >剩下最後 ${e.group} 組</small
              >
              <p class="mb-0 fw-medium d-flex align-items-center">
                TWD<span class="fs-2 ms-1">$${e.price}</span>
              </p>
            </div>
          </div>
        </div>`;
        cardsHtml += template;
      });
      document.querySelector('.card-list').innerHTML = cardsHtml;
      // 渲染篩選筆數
      const filterNum = document.querySelector('#filterNum');
      filterNum.textContent = `本次搜尋共 ${renderData.length} 筆資料`;
    },
    getData() {
      this.axios
        .get(
          'https://raw.githubusercontent.com/hexschool/js-training/main/travelApi.json'
        )
        .then((res) => {
          this.data.push(...res.data.data);
          // 渲染畫面
          this.render();
        })
        .catch((err) => {
          console.log(err.response);
        });
    },
  },
  mounted() {
    // 取 DON
    const form = document.querySelector('form');
    const submitBtn = document.querySelector('#submit');
    const areaFilter = document.querySelector('#areaFilter');
    // 監聽按鈕
    submitBtn.addEventListener('click', () => {
      window.event.preventDefault();
      form.querySelectorAll('input, select, textarea').forEach((e) => {
        this.newPackage[e.name] = e.value;
      });
      this.newPackage.id = this.data.length;
      this.data.push({ ...this.newPackage });
      this.render();
    });
    // 監聽下拉選單
    areaFilter.addEventListener('change', (e) => {
      this.render(e.target.value);
    });
    // 取得遠端資料
    this.getData();
  },
};
</script>

<template>
  <div class="container" style="padding-top: 120px; padding-bottom: 100px">
    <div class="row justify-content-center">
      <div class="col-10">
        <div class="shadow rounded-1" style="padding: 60px 0">
          <div class="row justify-content-center">
            <div class="col-5 w-40 d-none d-lg-block">
              <img src="/main_img.png" alt="主視覺" class="img-fluid pb-3" />
              <h1 class="logo mb-0 mt-1">Let's Travel!</h1>
            </div>
            <div class="col-10 col-lg-5 w-md-40">
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
                    <div class="col-xl-3">
                      <label
                        for="packageName"
                        class="col-form-label fw-medium text-primary"
                        >套票名稱</label
                      >
                    </div>
                    <div class="col-xl-9">
                      <input
                        type="text"
                        name="name"
                        id="packageName"
                        class="form-control border-bottom rounded-top-1"
                        placeholder="請填寫套票名稱"
                      />
                    </div>
                  </div>
                  <div class="row align-items-center pt-4">
                    <div class="col-xl-3">
                      <label
                        for="packageUrl"
                        class="col-form-label fw-medium text-primary"
                        >圖片網址</label
                      >
                    </div>
                    <div class="col-xl-9">
                      <input
                        type="url"
                        name="imgUrl"
                        id="packageUrl"
                        class="form-control border-bottom rounded-top-1"
                        placeholder="請填寫圖片網址"
                      />
                    </div>
                  </div>
                  <div class="row align-items-center pt-4">
                    <div class="col-xl-3">
                      <label
                        for="packArea"
                        class="col-form-label fw-medium text-primary"
                        >景點地區</label
                      >
                    </div>
                    <div class="col-xl-9 select-icon position-relative">
                      <select
                        id="packArea"
                        name="area"
                        class="form-select border-bottom rounded-top-1"
                      >
                        <option disabled selected hidden>請選擇景點地區</option>
                        <option value="台北">台北</option>
                        <option value="台中">台中</option>
                        <option value="高雄">高雄</option>
                      </select>
                    </div>
                  </div>
                  <div class="row align-items-center pt-4">
                    <div class="col-xl-3">
                      <label
                        for="packagePrice"
                        class="col-form-label fw-medium text-primary"
                        >套票金額</label
                      >
                    </div>
                    <div class="col-xl-9">
                      <input
                        type="number"
                        name="price"
                        id="packagePrice"
                        min="1"
                        class="form-control border-bottom rounded-top-1"
                        placeholder="請填寫套票金額"
                      />
                    </div>
                  </div>
                  <div class="row align-items-center pt-4">
                    <div class="col-xl-3">
                      <label
                        for="packageNum"
                        class="col-form-label fw-medium text-primary"
                        >套票組數</label
                      >
                    </div>
                    <div class="col-xl-9">
                      <input
                        type="number"
                        name="group"
                        id="packageNum"
                        min="1"
                        class="form-control border-bottom rounded-top-1"
                        placeholder="請填寫套票組數"
                      />
                    </div>
                  </div>
                  <div class="row align-items-center pt-4">
                    <div class="col-xl-3">
                      <label
                        for="packageStarts"
                        class="col-form-label fw-medium text-primary"
                        >套票星級</label
                      >
                    </div>
                    <div class="col-xl-9">
                      <input
                        type="number"
                        name="rate"
                        min="1"
                        max="10"
                        id="packageStarts"
                        class="form-control border-bottom rounded-top-1"
                        placeholder="請填寫套票星級"
                      />
                    </div>
                  </div>
                  <div class="row pt-4">
                    <div class="col-xl-3">
                      <label
                        for="packageDescribe"
                        class="col-form-label fw-medium text-primary"
                        >套票描述</label
                      >
                    </div>
                    <div class="col-xl-9">
                      <textarea
                        class="form-control border-bottom rounded-top-1"
                        name="description"
                        id="packageDescribe"
                        style="padding-bottom: 89px"
                        placeholder="請填寫套票描述（限 100 字）"
                      ></textarea>
                    </div>
                  </div>
                  <div class="row">
                    <div class="col-sm-6 ms-auto">
                      <button
                        type="submit"
                        id="submit"
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
        <div class="col-6 col-xl-4">
          <div class="row justify-content-end mt-1">
            <div class="col col-xl-9 select-icon position-relative">
              <select
                class="form-select bg-white border border-gray-500 rounded-1"
                id="areaFilter"
              >
                <option disabled hidden selected>地區搜尋</option>
                <option value="全部地區">全部地區</option>
                <option value="台北">台北</option>
                <option value="台中">台中</option>
                <option value="高雄">高雄</option>
              </select>
            </div>
          </div>
        </div>
        <div class="col-6 col-md-3">
          <span class="text-secondary" id="filterNum"></span>
        </div>
      </div>
      <div class="row card-list gy-5"></div>
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
.w-md-40 {
  @media (min-width: 992px) width: 40% !important;
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
.gy-5 {
  --bs-gutter-y: 38px;
}
.badge {
  line-height: 1.2;
  border-radius: 0 4px 4px 0;
}
option {
  appearance: none;
  -moz-appearance: none;
  -webkit-appearance: none;
  color: #212529;
}
</style>
