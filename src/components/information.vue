<template>
  <div class="container">
    <hr />

    <div class="row">
      <div class="col-md-4 col-sm-4" v-for="(list, index) in getProductArr" :key="index">
        <b-card
          :title="list.nameProduct"
          :img-src="list.picProduct"
          style="max-width: 20rem"
          class="mb-2 text-center"
        >
          <b-card-text>ราคา&nbsp;{{ list.price }}&nbsp;บาท</b-card-text>

          <b-button href="#" variant="dark" @click="addCart(list)">Add to cart</b-button>
        </b-card>
      </div>
    </div>
    <hr />

    <table class="table table-hover" v-for="(item,index) in cart" :key="index">
      <thead>
        <tr>
          <th scope="col">picture</th>
          <th scope="col">Name</th>
          <th scope="col">quantity</th>
          <th scope="col">price</th>
          <th scope="col">total</th>
          <th scope="col">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>
            <img :src="item.pic" width="60px" height="80px" />
          </td>
          <td>{{item.name}}</td>
          <td>
            <i class="fa fa-minus minus" @click="minusQty(item)"></i>
            {{item.quantity}}
            <i class="fa fa-plus plus" @click="plusQty(item)"></i>
          </td>

          <td>{{item.price}}</td>
          <td>{{item.total}}</td>
          <b-button @click="removeProduct(item)">ลบ</b-button>
        </tr>
      </tbody>
    </table>
    <h4 class="price text-center" v-if="cart!=0">ยอดชำระเงินทั้งหมด&nbsp;{{total()}}&nbsp;บาท</h4>
  </div>
</template>

<script>
export default {
  name: "Product",
  data() {
    return {
      cart: [],
      p1: 0,
      p2: 0,
      p3: 0,
      p4: 0,
      p5: 0,
      p6: 0,
      p7: 0,
      p8: 0,
    };
  },

  methods: {
    addCart: function (list) {
      var found;
      if (list.id == 1) {
        this.p1 += 1;
        if (this.p1 <= 1) {
          this.pushList(list);
        } else {
          found = this.findID(list);
          this.cart[found].quantity += 1;
          this.cart[found].total =
            this.cart[found].quantity * this.cart[found].price;
        }
      } else if (list.id == 2) {
        this.p2 += 1;
        if (this.p2 <= 1) {
          this.pushList(list);
        } else {
          found = this.findID(list);
          this.cart[found].quantity += 1;
          this.cart[found].total =
            this.cart[found].quantity * this.cart[found].price;
        }
      } else if (list.id == 3) {
        this.p3 += 1;
        if (this.p3 <= 1) {
          this.pushList(list);
        } else {
          found = this.findID(list);
          this.cart[found].quantity += 1;
          this.cart[found].total =
            this.cart[found].quantity * this.cart[found].price;
        }
      } else if (list.id == 4) {
        this.p4 += 1;
        if (this.p3 <= 1) {
          this.pushList(list);
        } else {
          found = this.findID(list);
          this.cart[found].quantity += 1;
          this.cart[found].total =
            this.cart[found].quantity * this.cart[found].price;
        }
      } else if (list.id == 5) {
        this.p5 += 1;
        if (this.p5 <= 1) {
          this.pushList(list);
        } else {
          found = this.findID(list);
          this.cart[found].quantity += 1;
          this.cart[found].total =
            this.cart[found].quantity * this.cart[found].price;
        }
      } else if (list.id == 6) {
        this.p6 += 1;
        if (this.p6 <= 1) {
          this.pushList(list);
        } else {
          found = this.findID(list);
          this.cart[found].quantity += 1;
          this.cart[found].total =
            this.cart[found].quantity * this.cart[found].price;
        }
      } else if (list.id == 7) {
        this.p7 += 1;
        if (this.p7 <= 1) {
          this.pushList(list);
        } else {
          found = this.findID(list);
          this.cart[found].quantity += 1;
          this.cart[found].total =
            this.cart[found].quantity * this.cart[found].price;
        }
      } else if (list.id == 8) {
        this.p8 += 1;
        if (this.p8 <= 1) {
          this.pushList(list);
        } else {
          found = this.findID(list);
          this.cart[found].quantity += 1;
          this.cart[found].total =
            this.cart[found].quantity * this.cart[found].price;
        }
      }
    },
    pushList(list) {
      this.cart.push({
        id: list.id,
        pic: list.picProduct,
        name: list.nameProduct,
        quantity: 1,
        price: list.price,
        total: list.price,
      });
    },
    findID: function (list) {
      for (var i = 0; i < this.cart.length; i++) {
        if (this.cart[i].id == list.id) {
          return i;
        }
      }
      return -1;
    },
    minusQty: function (item) {
      item.quantity -= 1;
      if (item.quantity <= 1) {
        item.quantity = 1;
      }
      item.total = item.quantity * item.price;
    },
    plusQty: function (item) {
      item.quantity += 1;
      item.total = item.quantity * item.price;
    },
    removeProduct(item) {
      if (confirm("คุณต้องการลบหรือไม่ ?")) {
        var index = this.cart.indexOf(item);
        this.cart.splice(index, 1);
      }
    },
    total: function () {
      var sum = 0;
      this.cart.forEach(function (item) {
        sum += item.total;
      });
      return sum;
    },
  },
  computed: {
    getProductArr() {
      return this.$store.getters.getProduct;
    },
  },
};
</script>

<style scoped>
</style>
