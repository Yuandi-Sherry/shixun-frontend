<template>
  <div>
    <el-tabs v-model="currentTab" :tab-position="tabPosition" class="page">
      <!-- <el-tab-pane v-for="tab in tabs" :key="tab.id" :label="tab.label">
      </el-tab-pane> -->
      <el-tab-pane label="分析结果"> 分析结果
          <tab-sa/>
      </el-tab-pane>

      <el-tab-pane label="抠图"> 抠图
          <tab-cutout/>
      </el-tab-pane>

      <el-tab-pane label="虚化"> 虚化
          <tab-bokeh/>
      </el-tab-pane>

      <el-tab-pane label="弹幕"> 弹幕
          <tab-barrage/>
      </el-tab-pane>
      <!-- <component class="page" :is="currentTabComponent"> </component> -->
    </el-tabs>

  </div>
</template>
<script>
    import tabBokeh from './tab-bokeh.vue'
    import tabCutout from './tab-cutout.vue'
    import tabBarrage from './tab-barrage.vue'
    import tabSA from './tab-sa.vue'
    export default {
        name: "tabs",
        data() {
            return {
                currentTab: "1",
                tabPosition: 'top',
                tabs: [
                    {
                        id: 4,
                        name: "sa",
                        label: "显著性分析",
                        isActive: false
                    },
                    {
                        id: 0,
                        name: "bokeh",
                        label: "背景虚化",
                        isActive: true
                    }, {
                        id: 1,
                        name: "cutout",
                        label: "抠图",
                        isActive: false
                    }, {
                        id: 2,
                        name: "barrage",
                        label: "弹幕",
                        isActive: false
                    }
                ]
            };
        },
        computed: {
            currentTabComponent: function () {
                return 'tab-' + this.tabs[this.currentTab].name.toLowerCase()
            }
        },
        components: {
            "tab-bokeh": tabBokeh,
            "tab-cutout": tabCutout,
            "tab-barrage": tabBarrage,
            "tab-sa": tabSA
        }
    };

</script>

<style scoped>
    .page {
        display: flex;
        flex-direction: column;
        justify-content: center;
        margin-left: 10px;
        align-items: center;
    }
</style>
