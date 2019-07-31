<template>
    <div style="padding:20px;">
        <el-tree
            :data="data"
            show-checkbox
            node-key="id"
            default-expand-all
            :expand-on-click-node="false"
        >
            <span class="custom-tree-node" slot-scope="{ node, data }">
                <span>{{ node.label }}</span>
                <span>
                    <el-button type="text" size="mini" @click="() => append(data)">增加</el-button>
                    <el-button type="text" size="mini" @click="() => remove(node, data)">删除</el-button>
                </span>
            </span>
        </el-tree>
    </div>
</template>

<script>
export default {
    data() {
        const data = [
            {
                id: 1,
                label: "一级 1",
                children: [
                    {
                        id: 4,
                        label: "二级 1-1",
                        children: [
                            {
                                id: 9,
                                label: "三级 1-1-1"
                            },
                            {
                                id: 10,
                                label: "三级 1-1-2"
                            }
                        ]
                    }
                ]
            },
            {
                id: 2,
                label: "一级 2",
                children: [
                    {
                        id: 5,
                        label: "二级 2-1"
                    },
                    {
                        id: 6,
                        label: "二级 2-2"
                    }
                ]
            },
            {
                id: 3,
                label: "一级 3",
                children: [
                    {
                        id: 7,
                        label: "二级 3-1"
                    },
                    {
                        id: 8,
                        label: "二级 3-2"
                    }
                ]
            }
        ];
        return {
            data: JSON.parse(JSON.stringify(data))
        };
    },
    mounted() {},
    methods: {
        setSectionHeight() {
            this.$nextTick(() => {
                this.$refs.shareContainer.style.height =
                    document.body.clientHeight - 160 + "px";
            });
        },
        hideWxCodeModal() {
            this.wxModal.show = false;
        },
        // 分享到微信，显示微信二维码弹框；
        shareToWeixin() {
            this.wxModal.show = true;
        },
        shareToQQ() {
            this.shareConfig("qq");
        },
        shareToQQzone() {
            this.shareConfig("qqZone");
        },
        shareToWeibo() {
            this.shareConfig("weibo");
        },
        shareToDouban() {
            this.shareConfig("douban");
        }
    }
};
</script>

<style scoped>
.custom-tree-node {
    flex: 1;
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 16px;
    padding-right: 8px;
}
</style>
