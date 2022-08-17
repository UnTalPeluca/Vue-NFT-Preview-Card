<template>
  <div class="card">
    <div class="card__product-img">
      <img 
        class="card__img"
        alt="product-image" 
        :src="require('@/static/images/' + img)"
      >
    </div>
    <div class="card__content">
      <p class="card__name">{{ name }} <span v-if="id">#{{ id }}</span></p>
      <p class="card__description" v-if="description">{{ description }}</p>
      <div class="card__content-bottom">
        <div class="card__price">
          <div class="icon">
            <img src="@/assets/images/nft-card/icon-ethereum.svg" alt="">
          </div>
          <p>{{ price }} ETH</p>
        </div>
        <div v-if="time" class="card__time">
          <div class="icon">
            <img src="@/assets/images/nft-card/icon-clock.svg" alt="">
          </div>
          <p>{{ time }} days left</p>
        </div>
      </div>
    </div>
    <div class="card__footer">
      <div class="card__avatar">
        <img :src="require('@/static/images/' + avatar)" alt="avatar-image">
      </div>
      <p class="card__autor">Creation of <span class="card__autor--alt-color">{{ autor }}</span></p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    img: {
      type: String,
      default: '',
      required: true
    },
    name: {
      type: String,
      default: '',
      required: true
    },
    description: {
      type: String,
      default: ''
    },
    id: {
      type: [String, Number],
      default: null
    },
    price: {
      type: Number,
      default: 0,
      required: true
    },
    time: {
      type: [String, Number],
      default: ''
    },
    autor: {
      type: String,
      default: ''
    },
    avatar: {
      type: String,
      default: '',
    },
  },
}
</script>

<style scoped lang="scss">
.icon {
  display: flex;
}
.card {
  background-color: #15263F;
  color: #8BACD9;
  border-radius: 16px;
  padding: 24px;
  width: 327px;
  font-size: 1.5rem;
  box-shadow: 0 25px 50px 0 rgba(0,0,0,0.1);
  @media screen and (min-width: 768px) {
    font-size: 1.6rem;
    width: 350px;
    padding-bottom: 32px;
  }
  .card__product-img {
    cursor: pointer;
    position: relative;
    border-radius: 8px;
    overflow: hidden;
    @mixin hoverOpacity {
      content: "";
      position: absolute;
      left: 0;
      width: 100%;
      height: 100%;
      opacity: 0;
      transition: opacity 0.25s ease-out;
    }
    &::after {
      @include hoverOpacity;
      background: no-repeat rgba(0, 255, 255, 0.5) url(../../assets/images/nft-card/icon-view.svg) center;
    }
    &:hover {
      &::after {
        opacity: 1;
      }
    }
  }
  .card__content {
    display: flex;
    flex-direction: column;
    gap: 12px;
    padding: 24px 0 16px 0;
    @media screen and (min-width: 768px) {
      gap: 16px;
      padding: 24px 0;
    }
    .card__name {
      color: white;
      font-size: 2.2rem;
      font-weight: bold;
      cursor: pointer;
      &:hover {
        color: #00FFF8;
      }
    }
    .card__description {
      font-size: 1.8rem;
      line-height: 2.6rem;
      font-weight: lighter;
    }
    .card__content-bottom {
      display: flex;
      justify-content: space-between;
      padding-top: 4px;
      @media screen and (min-width: 768px) {
        padding-top: 6px;
      }
      > * {
        display: flex;
        align-items: center;
        gap: 8px;
        font-weight: 600;
      }
      .card__price {
        color: #00FFF8;
      }
    }
  }
  .card__footer {
    display: flex;
    align-items: center;
    border-top: 1px solid #2E405A;
    gap: 16px;
    padding-top: 16px;
    .card__avatar {
      display: flex;
      border-radius: 90px;
      border: 1px solid white;
      img {
        width: 33px;
      }
    }
    .card__autor--alt-color {
      color: white;
      cursor: pointer;
      &:hover {
        color: #00FFF8;
      }
    }
  }
}

//Transition
.fade-enter-active,
.fade-leave-active {
    transition: 0.25s ease-out;
}
.fade-leave-to,
.fade-enter-from {
  opacity: 0;
}
</style>
