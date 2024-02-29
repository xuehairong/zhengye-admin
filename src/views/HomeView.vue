<script setup>
import { reactive, toRaw, ref } from 'vue';
const formState = reactive({
  no: '',
  delivery: false,
  type: [],
  resource: '',
  desc: ''
});
const labelCol = {
  style: {
    width: '80px'
  }
};
const dataSource = [
  {
    key: '1',
    no: '指定渠道编码',
    name: 32,
    province: '西湖区湖底公园1号'
  },
  {
    key: '2',
    no: '胡彦祖',
    name: 42,
    province: '西湖区湖底公园1号'
  }
];
const columns = [
  {
    title: '指定渠道编码',
    dataIndex: 'no',
    key: 'no'
  },
  {
    title: '指定渠道名称',
    dataIndex: 'name',
    key: 'na me'
  },
  {
    title: '所在省',
    dataIndex: 'province',
    key: 'province'
  }
];
const daterange = ref(['2015/01/01', '2015/01/01']);
</script>

<template>
  <header class="bg-white py-4 px-8">
    <a-breadcrumb>
      <a-breadcrumb-item>首页</a-breadcrumb-item>
      <a-breadcrumb-item>年度协议管理</a-breadcrumb-item>
      <a-breadcrumb-item>二级商协议</a-breadcrumb-item>
      <a-breadcrumb-item>新增二级商协议</a-breadcrumb-item>
    </a-breadcrumb>
    <div class="text-xl mt-2">新增二级商协议</div>
  </header>
  <main class="px-4">
    <a-divider dashed
      ><div class="divider">1</div>
      <span>协议主体</span></a-divider
    >
    <div class="bg-white rounded px-4 py-2">
      <a-form :model="formState" :label-col="labelCol">
        <a-form-item label="协议客户" :rules="[{ required: true, message: '请选择客户' }]">
          <a-button>选择客户</a-button>
          <span class="ml-2">上海正也医药有限公司</span>
        </a-form-item>
        <a-form-item label="购进指标">
          <a-select
            class="mr-2"
            ref="select"
            value="money"
            style="width: 90px; display: inline-block"
            @focus="focus"
            @change="handleChange"
          >
            <a-select-option value="money">金额</a-select-option>
          </a-select>
          <a-input style="width: 360px" placeholder="输入金额/数量" />
        </a-form-item>
        <a-form-item label="销售区域">
          <a-button>选择区域</a-button>
          <a-tag class="ml-2" closable color="blue">全国</a-tag>
        </a-form-item>
        <a-form-item label="购进渠道">
          <div class="mb-2">
            <a-select
              ref="select"
              value="money"
              style="width: 100px; display: inline-block"
              @focus="focus"
              @change="handleChange"
            >
              <a-select-option value="money">指定渠道</a-select-option>
            </a-select>
            <a-button class="ml-2">请选择渠道</a-button>
          </div>
          <a-table :dataSource="dataSource" :columns="columns" :pagination="false" />
        </a-form-item>
      </a-form>
    </div>
    <a-divider dashed
      ><div class="divider">2</div>
      <span>产品政策</span></a-divider
    >
    <div class="flex items-center flex-wrap gap-4 mb-4">
      <a-button type="primary">添加产品</a-button>
      <div><span>购进总指标（万元）：</span><span>¥152.65</span></div>
      <div>
        <span>指标按季度分解（万元）：</span
        ><span>【Q1】￥12.5，【Q2】￥12.5，【Q3】￥12.5， 【Q4】￥12.5</span>
      </div>
      <div><span>纯销总指标（万元）：</span><span>￥152.65</span></div>
    </div>
    <div class="bg-white rounded p-4">
      <div class="flex items-center flex-wrap gap-4">
        <div>
          产品：<a-button>选择产品</a-button><span class="ml-2 text-blue-500">美复胶丸</span
          ><span class="ml-2 text-blue-500">24粒/盒</span>
        </div>
        <div>协议效期： <a-range-picker /></div>
      </div>
      <a-divider />
      <a-descriptions
        bordered
        :column="{ xxl: 7, xl: 7, lg: 4, md: 4, sm: 3, xs: 2 }"
        layout="vertical"
      >
        <a-descriptions-item label="协议价（元）">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="票折（元）">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="购进指标量（大单位）">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="购进指标量（小单位）">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="购进金额（万元）">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="纯销指标量（小单位）">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="纯销指标金额（万元）">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
      </a-descriptions>
      <a-descriptions
        bordered
        :column="{ xxl: 8, xl: 8, lg: 4, md: 4, sm: 3, xs: 2 }"
        layout="vertical"
        class="mt-4"
      >
        <a-descriptions-item label="分销奖 ">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="费用科目">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="零售配送">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="费用科目">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="医疗配送商">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="费用科目">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="自定义7">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
        <a-descriptions-item label="自定义8">
          <a-input placeholder="请输入" />
        </a-descriptions-item>
      </a-descriptions>
    </div>
    <a-divider dashed
      ><div class="divider">3</div>
      <span>补充协议</span></a-divider
    >
    <div class="mb-10">
      <a-tabs v-model:activeKey="activeKey" type="card">
        <a-tab-pane key="1" tab="补充协议1" class="bg-white p-4">
          <p class="mb-4">协议内容：</p>
          <a-textarea :rows="4" />
        </a-tab-pane>
        <a-tab-pane key="2" tab="补充协议2" class="bg-white p-4">
          <p class="mb-4">协议内容：</p>
          <a-textarea :rows="4" />
        </a-tab-pane>
        <a-tab-pane key="3" tab="补充协议3" class="bg-white p-4">
          <p class="mb-4">协议内容：</p>
          <a-textarea :rows="4" />
        </a-tab-pane>
      </a-tabs>
    </div>
  </main>
  <div class="bg-white p-4">
    <a-button type="primary">保存</a-button>
  </div>
</template>
<style scoped>
.divider {
  @apply bg-blue-500 rounded-full w-6 inline-block text-white mr-2;
}
.ant-tag {
  height: 32px;
  line-height: 32px;
  font-size: 14px;
}
:deep(.ant-tag-close-icon) {
  margin-left: 12px;
  color: #0958d9;
  vertical-align: middle;
}
input[type='text'],
textarea {
  background-color: #f8f8f8;
}
:deep(.ant-table-cell) {
  padding: 6px !important;
}
:deep(
    :where(.css-dev-only-do-not-override-1hsjdkk).ant-descriptions.ant-descriptions-bordered
      .ant-descriptions-item-label
  ) {
  padding: 6px;
  border-inline-end: none;
}
:deep(
    :where(.css-dev-only-do-not-override-1hsjdkk).ant-descriptions.ant-descriptions-bordered
      .ant-descriptions-item-content
  ) {
  padding: 6px;
  border-inline-end: none;
}
:deep(:where(.css-dev-only-do-not-override-1hsjdkk).ant-tabs-top > .ant-tabs-nav) {
  margin: 0;
}
:deep(.ant-select-arrow) {
  color: #4e8bfe;
}
</style>
