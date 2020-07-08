<template>
  <view class="box">
    <view
      @click="onClick_1"
      :data-url="item.url"
      :key="item.index"
      v-for="(item, index) in data"
      ><view class="bd"
        ><image
          class="layer"
          src="https://img.alicdn.com/tfs/TB1bLoWoYH1gK0jSZFwXXc7aXXa-684-684.png"
        />
        <image class="bg" :src="item.coverImage" />
        <view class="wrap"
          ><image
            class="riverdinwei"
            src="https://img.alicdn.com/tfs/TB1mtZRoVT7gK0jSZFpXXaTkpXa-28-36.png"
          />
          <text class="distance">距离500m</text>
        </view></view
      ><view class="main"
        ><text class="title">{{ item.title }}</text> </view
      ><view class="ft"
        ><view class="block"
          ><image
            class="xianjin"
            src="https://img.alicdn.com/tfs/TB1OvsYoW61gK0jSZFlXXXDKFXa-60-60.png"
          />
          <text class="fashionHome">{{ item.user.userName }}</text> </view
        ><view v-if="isReadCountShow(item.readCount)" class="group"
          ><image
            class="favorite"
            src="https://img.alicdn.com/tfs/TB1arwYo7T2gK0jSZFkXXcIQFXa-46-44.png"
          />
          <text class="num">{{ item.readCount }}</text>
        </view></view
      ></view
    ></view
  >
</template>
<script>
import { fetch } from 'whatwg-fetch';
import jsonp from 'fetch-jsonp';
export default {
  data() {
    return {
      data: [
        {
          title: '小户型卫浴怎样才能装得高大上？',
          coverImage:
            'https://img.alicdn.com/tfs/TB1Txq6o7T2gK0jSZFkXXcIQFXa-684-684.png',
          readCount: 200,
          user: {
            userImage:
              'https://img.alicdn.com/tfs/TB1DWe6oYj1gK0jSZFOXXc7GpXa-60-60.png',
            userName: '时尚家居'
          },
          url: 'https://www.imgcook.com'
        },
        {
          title: '拥有超多功能的40平米简约小公寓了解一下',
          coverImage:
            'https://img.alicdn.com/tfs/TB1XRQTo7P2gK0jSZPxXXacQpXa-684-648.png',
          readCount: 500,
          user: {
            userImage:
              'https://img.alicdn.com/tfs/TB1DWe6oYj1gK0jSZFOXXc7GpXa-60-60.png',
            userName: '花花设计工作'
          },
          url: 'https://www.imgcook.com/docs'
        }
      ],
      constants: {}
    };
  },
  methods: {
    isReadCountShow(readCount) {
      return readCount > 300;
    },
    fetch_example() {
      fetch('https://jsonplaceholder.typicode.com/todos/1', {
        method: 'GET',
        headers: '{"Content-Type":"json"}'
      })
        .then(response => response.json())
        .then((data, error) => {
          console.log('fetch example: ', data, error);
          return data;
        })
        .catch(e => {
          console.log('error', e);
        });
    },
    jsonp_example() {
      jsonp('https://assets.airbnb.com/frontend/search_results.js', {
        jsonpCallbackFunction: 'search_results',
        body: {}
      })
        .then(response => response.json())
        .then((data, error) => {
          console.log('jsonp example: ', data, error);
          return data;
        })
        .catch(e => {
          console.log('error', e);
        });
    },
    onClick_1(e) {
      window.open(this.item.url, '_blank');
    }
  },
  created() {
    console.log('super props');
    this.fetch_example();
    this.jsonp_example();
  },
  updated() {}
};
</script>
<style scoped>
.box {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: flex-start;
  height: 1068rpx;
}

.bd {
  display: flex;
  position: relative;
  align-items: flex-start;
  flex-direction: row;
  opacity: 1;
  width: 684rpx;
  height: 684rpx;
}

.layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 684rpx;
  height: 684rpx;
  overflow: hidden;
}

.bg {
  position: absolute;
  top: 0;
  left: 0;
  opacity: 1;
  width: 684rpx;
  height: 684rpx;
}

.wrap {
  box-sizing: border-box;
  display: flex;
  position: relative;
  align-items: center;
  flex-direction: row;
  margin-top: 36rpx;
  margin-left: 36rpx;
  border-radius: 30rpx;
  background-color: rgba(0, 0, 0, 0.4);
  padding-right: 18rpx;
  padding-left: 20rpx;
  height: 60rpx;
}

.riverdinwei {
  opacity: 1;
  width: 28rpx;
  height: 36rpx;
}

.distance {
  margin-left: 8rpx;
  height: 44rpx;
  font-weight: 400;
  font-size: 36rpx;
  color: #ffffff;
  line-height: 44rpx;
  white-space: nowrap;
}

.main {
  display: flex;
  align-items: flex-start;
  flex-direction: row;
  justify-content: center;
  background-color: #ffffff;
  width: 684rpx;
  height: 228rpx;
}

.title {
  margin-top: 44rpx;
  width: 600rpx;
  height: 176rpx;
  font-weight: 400;
  font-size: 60rpx;
  color: #333333;
  line-height: 88rpx;
  overflow: hidden;
  text-overflow: ellipsis;
}

.ft {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  flex-direction: row;
  justify-content: space-between;
  border-bottom-left-radius: 24rpx;
  border-bottom-right-radius: 24rpx;
  background-color: #ffffff;
  padding-right: 34rpx;
  padding-left: 36rpx;
  width: 684rpx;
  height: 156rpx;
  overflow: hidden;
}

.block {
  display: flex;
  align-items: center;
  flex-direction: row;
  height: 60rpx;
}

.xianjin {
  width: 60rpx;
  height: 60rpx;
}

.fashionHome {
  margin-left: 12rpx;
  height: 56rpx;
  font-weight: 300;
  font-size: 48rpx;
  color: #666666;
  line-height: 56rpx;
  white-space: nowrap;
}

.group {
  display: flex;
  align-items: center;
  flex-direction: row;
  height: 60rpx;
}

.favorite {
  width: 44rpx;
  height: 44rpx;
}

.num {
  margin-left: 10rpx;
  height: 52rpx;
  font-weight: 400;
  font-size: 44rpx;
  color: #999999;
  line-height: 52rpx;
  white-space: nowrap;
}
</style>
