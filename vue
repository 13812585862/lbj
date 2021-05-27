vue组件信息传递：
1父组件通过传递函数:addTodo='addTodo',子组件通过props拿到addTodo函数，通过this.addTodo执行
2.通过父组件绑定监听函数@addTodo="addTodo"，子组件通过this.$emit('addTodo',todo)调用
3.通过父组件在mounted的时候绑定事件监听this.$refs.header.$on('addTodo',this.addTodo)（注意：this.sddTodo是父组件的函数）
4.PubSub.subscribe('addTodo',(msg,data)=>{  (注意箭头函数化解this指向问题)
 this.addTodo(data)
})
5.slot传递标签数据，slot是在父组件里运行编译的，相关代码都放到父组件里，（我的理解是父组件都搞定了，子组件需要引入即可）
父组件<todo-footer><input type="checkbox" v-model="isAllCheck" slot="checkAll"></todo-footer>子组件<slot name="checkAll"></slot>
