<script>
export default {
  data() {
    return {
      data: [
        {
          id: 0,
          name: '肥宅心碎賞櫻3日',
          imgUrl:
            'https://images.unsplash.com/photo-1522383225653-ed111181a951?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1655&q=80',
          area: '高雄',
          description: '賞櫻花最佳去處。肥宅不得不去的超讚景點！',
          group: 87,
          price: 1400,
          rate: 10,
        },
        {
          id: 1,
          name: '貓空纜車雙程票',
          imgUrl:
            'https://images.unsplash.com/photo-1501393152198-34b240415948?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1650&q=80',
          area: '台北',
          description:
            '乘坐以透明強化玻璃為地板的「貓纜之眼」水晶車廂，享受騰雲駕霧遨遊天際之感',
          group: 99,
          price: 240,
          rate: 2,
        },
        {
          id: 2,
          name: '台中谷關溫泉會1日',
          imgUrl:
            'https://images.unsplash.com/photo-1535530992830-e25d07cfa780?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1650&q=80',
          area: '台中',
          description:
            '全館客房均提供谷關無色無味之優質碳酸原湯，並取用八仙山之山冷泉供蒞臨貴賓沐浴及飲水使用。',
          group: 20,
          price: 1765,
          rate: 7,
        },
      ],
      template: '',
    };
  },
  methods: {
    render() {
      // const card = document.querySelector('.card').parentElement;
      // console.log(card.querySelector('.card-title'));
      this.data.forEach((e) => {
        const text = `
        <div class="col-4">
          <div class="card shadow border-gray-300 h-100">
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
        this.template += text;
      });
      document.querySelector('.card-list').innerHTML = this.template;
    },
  },
  mounted() {
    this.render();
  },
};
</script>

<style>
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
