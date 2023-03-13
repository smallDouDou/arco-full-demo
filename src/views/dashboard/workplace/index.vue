<template>
  <a-card class="chat-card-box" hoverable>
    <div class="table-box">
      <div class="table-content">
        <a-table
          :columns="columns"
          :data="data"
          :bordered="{ wrapper: true, cell: true }"
          :pagination="pagination"
          :scroll="{ x: 2000, y: '100%' }"
          table-layout-fixed
        />
      </div>
    </div>
  </a-card>
  <div class="container">
    <div class="left-side">
      <div class="panel">
        <Banner />
        <DataPanel />
        <ContentChart />
      </div>
      <a-grid :col-gap="16" :cols="24" :row-gap="16" style="margin-top: 16px">
        <a-grid-item
          :span="{ xs: 24, sm: 24, md: 24, lg: 12, xl: 12, xxl: 12 }"
        >
          <PopularContent />
        </a-grid-item>
        <a-grid-item
          :span="{ xs: 24, sm: 24, md: 24, lg: 12, xl: 12, xxl: 12 }"
        >
          <CategoriesPercent />
        </a-grid-item>
      </a-grid>
    </div>
    <div class="right-side">
      <a-grid :cols="24" :row-gap="16">
        <a-grid-item :span="24">
          <div class="panel moduler-wrap">
            <QuickOperation />
            <RecentlyVisited />
          </div>
        </a-grid-item>
        <a-grid-item :span="24" class="panel">
          <Carousel />
        </a-grid-item>
        <a-grid-item :span="24" class="panel">
          <Announcement />
        </a-grid-item>
        <a-grid-item :span="24" class="panel">
          <Docs />
        </a-grid-item>
      </a-grid>
    </div>
  </div>
</template>

<script lang="ts" setup>
  import { reactive } from 'vue';
  import Banner from './components/banner.vue';
  import DataPanel from './components/data-panel.vue';
  import ContentChart from './components/content-chart.vue';
  import PopularContent from './components/popular-content.vue';
  import CategoriesPercent from './components/categories-percent.vue';
  import RecentlyVisited from './components/recently-visited.vue';
  import QuickOperation from './components/quick-operation.vue';
  import Announcement from './components/announcement.vue';
  import Carousel from './components/carousel.vue';
  import Docs from './components/docs.vue';

  const pagination = { pageSize: 20 };

  const columns = [
    {
      title: 'Name',
      dataIndex: 'name',
      fixed: 'left',
      width: 140,
    },
    {
      title: 'Salary',
      dataIndex: 'salary',
    },
    {
      title: 'Address',
      dataIndex: 'address',
    },
    {
      title: 'Address1',
      dataIndex: 'address1',
    },
    {
      title: 'Address2',
      width: 100,
      dataIndex: 'address2',
    },
    {
      title: 'Address3',
      width: 100,
      dataIndex: 'address3',
    },
    {
      title: 'Address4',
      width: 100,
      dataIndex: 'address4',
    },
    { title: 'OrderID', dataIndex: 'OrderID', width: 100, align: 'center' },
    { title: 'OrderDate', dataIndex: 'OrderDate', width: 100, align: 'center' },
    { title: 'Country', dataIndex: 'Country', width: 100, align: 'center' },
    { title: 'ASIN', dataIndex: 'ASIN', width: 100, align: 'center' },
    { title: 'MSKU', dataIndex: 'MSKU', width: 100, align: 'center' },
    {
      title: 'ProductName',
      dataIndex: 'ProductName',
      width: 100,
      align: 'center',
    },
    {
      title: 'RequestType',
      dataIndex: 'RequestType',
      width: 100,
      align: 'center',
    },
    {
      title: 'DetailedDescription',
      dataIndex: 'DetailedDescription',
      width: 120,
      align: 'center',
    },
    { title: 'Status', dataIndex: 'Status', width: 100, align: 'center' },
    {
      title: 'FinalSolution',
      dataIndex: 'FinalSolution',
      width: 100,
      align: 'center',
    },
    {
      title: 'RefundAmount',
      dataIndex: 'RefundAmount',
      width: 100,
      align: 'center',
    },
    {
      title: 'ReplacementOrder',
      dataIndex: 'ReplacementOrder',
      width: 100,
      align: 'center',
    },
    { title: 'Remark', dataIndex: 'Remark', width: 100, align: 'center' },
    {
      title: 'Email',
      dataIndex: 'email',
      fixed: 'right',
      width: 200,
    },
  ];

  const expandable = {
    title: 'Expand',
    width: 80,
  };

  const scroll = {
    x: 2000,
    y: 200,
  };

  const data = reactive([
    {
      key: '1',
      name: 'Jane Doe',
      salary: 23000,
      address: '32 Park Road, London',
      email: 'jane.doe@example.com',
      expand: 'Expand Content',
    },
    {
      key: '2',
      name: 'Alisa Ross',
      salary: 25000,
      address: '35 Park Road, London',
      email: 'alisa.ross@example.com',
    },
    {
      key: '3',
      name: 'Kevin Sandra',
      salary: 22000,
      address: '31 Park Road, London',
      email: 'kevin.sandra@example.com',
    },
    {
      key: '4',
      name: 'Ed Hellen',
      salary: 17000,
      address: '42 Park Road, London',
      email: 'ed.hellen@example.com',
    },
    {
      key: '5',
      name: 'William Smith',
      salary: 27000,
      address: '62 Park Road, London',
      email: 'william.smith@example.com',
    },
  ]);
</script>

<script lang="ts">
  export default {
    name: 'Dashboard', // If you want the include property of keep-alive to take effect, you must name the component
  };
</script>

<style lang="less" scoped>
  // 设置当前Card的高度
  .chat-card-box {
    display: flex;
    flex: 1;
    flex-direction: column;
    height: calc(100% - 32px);
  }
  .table-box {
    //display: flex;
    //flex-direction: column;
    flex: 1;
    height: 500px;
    //height: calc(100% - 32px - 12px - 32px - 12px - 16px);

    .table-content {
      //flex: 1;
      height: calc(100% - 16px);
    }
  }

  .container {
    background-color: var(--color-fill-2);
    padding: 16px 20px;
    padding-bottom: 0;
    display: flex;
  }

  .left-side {
    flex: 1;
    overflow: auto;
  }

  .right-side {
    width: 280px;
    margin-left: 16px;
  }

  .panel {
    background-color: var(--color-bg-2);
    border-radius: 4px;
    overflow: auto;
  }

  :deep(.panel-border) {
    margin-bottom: 0;
    border-bottom: 1px solid rgb(var(--gray-2));
  }

  .moduler-wrap {
    border-radius: 4px;
    background-color: var(--color-bg-2);

    :deep(.text) {
      font-size: 12px;
      text-align: center;
      color: rgb(var(--gray-8));
    }

    :deep(.wrapper) {
      margin-bottom: 8px;
      text-align: center;
      cursor: pointer;

      &:last-child {
        .text {
          margin-bottom: 0;
        }
      }

      &:hover {
        .icon {
          color: rgb(var(--arcoblue-6));
          background-color: #e8f3ff;
        }

        .text {
          color: rgb(var(--arcoblue-6));
        }
      }
    }

    :deep(.icon) {
      display: inline-block;
      width: 32px;
      height: 32px;
      margin-bottom: 4px;
      color: rgb(var(--dark-gray-1));
      line-height: 32px;
      font-size: 16px;
      text-align: center;
      background-color: rgb(var(--gray-1));
      border-radius: 4px;
    }
  }
</style>

<style lang="less" scoped>
  // responsive
  .mobile {
    .container {
      display: block;
    }

    .right-side {
      // display: none;
      width: 100%;
      margin-left: 0;
      margin-top: 16px;
    }
  }
</style>
