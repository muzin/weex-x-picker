<template>
    <div class="picker">

        <wxc-popup class="popup-wrapper"
                   popup-color="#ffffff"
                   :show="show"
                   @wxcPopupOverlayClicked="PopupOverlayClick"
                   pos="bottom"
                   width="750"
                   height="550">

            <div class="picker-content">

                <div class="picker-item" :style="pickerItemStyle">

                    <div class="picker-bar" :style="pickerBarStyle"></div>

                    <scroller class="picker-item-list"
                              show-scrollbar="false"
                              :ref="col_1_ref"
                              scroll-direction="vertical"
                              :style="pickerItemStyle" @scroll="onScroll" @scrollend="e => scrollEnd(e, col_1_ref)">

                        <text @disappear="e => disAppearPickItem(e, col_1_ref, 0)"
                              @appear="e => appearPickItem(e, col_1_ref, 0)"
                              :ref="col_1_ref + '_text_0'"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>
                        <text @disappear="e => disAppearPickItem(e, col_1_ref, 1)"
                              @appear="e => appearPickItem(e, col_1_ref, 1)"
                              :ref="col_1_ref + '_text_1'"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>

                        <text @disappear="e => disAppearPickItem(e, col_1_ref, index + 2)"
                              @appear="e => appearPickItem(e, col_1_ref, index + 2)"
                              :ref="col_1_ref + '_text_' + numAdd(index,2)"
                              v-for="(item, index) of col_1_list"
                              :key="col_1_ref + '_' + index"
                              class="picker-item-text"
                              :style="pickerItemTextStyle">{{ (item.title || '') }}
                        </text>

                        <text @disappear="e => disAppearPickItem(e, col_1_ref, col_1_list.length + 3)"
                              @appear="e => appearPickItem(e, col_1_ref, col_1_list.length + 3)"
                              :ref="col_1_ref + '_text_' + numAdd(col_1_list.length + 3)"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>
                        <text @disappear="e => disAppearPickItem(e, col_1_ref, col_1_list.length + 4)"
                              @appear="e => appearPickItem(e, col_1_ref, col_1_list.length + 4)"
                              :ref="col_1_ref + '_text_' + numAdd(col_1_list.length + 4)"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>

                    </scroller>

                </div>

                <div class="picker-item" :style="pickerItemStyle">

                    <div class="picker-bar" :style="pickerBarStyle"></div>

                    <scroller class="picker-item-list"
                              show-scrollbar="false"
                              :ref="col_2_ref"
                              scroll-direction="vertical"
                              :style="pickerItemStyle" @scroll="onScroll" @scrollend="e => scrollEnd(e, col_2_ref)">

                        <text @disappear="e => disAppearPickItem(e, col_2_ref, 0)"
                              @appear="e => appearPickItem(e, col_2_ref, 0)"
                              :ref="col_2_ref + '_text_0'"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>
                        <text @disappear="e => disAppearPickItem(e, col_2_ref, 1)"
                              @appear="e => appearPickItem(e, col_2_ref, 1)"
                              :ref="col_2_ref + '_text_1'"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>

                        <text @disappear="e => disAppearPickItem(e, col_2_ref, index + 2)"
                              @appear="e => appearPickItem(e, col_2_ref, index + 2)"
                              :ref="col_2_ref + '_text_' + numAdd(index,2)"
                              v-for="(item, index) of col_2_list"
                              :key="col_2_ref + '_' + index"
                              class="picker-item-text"
                              :style="pickerItemTextStyle">{{ (item.title || '') }}
                        </text>

                        <text @disappear="e => disAppearPickItem(e, col_2_ref, col_2_list.length + 3)"
                              @appear="e => appearPickItem(e, col_2_ref, col_2_list.length + 3)"
                              :ref="col_2_ref + '_text_' + numAdd(col_2_list.length + 3)"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>
                        <text @disappear="e => disAppearPickItem(e, col_2_ref, col_2_list.length + 4)"
                              @appear="e => appearPickItem(e, col_2_ref, col_2_list.length + 4)"
                              :ref="col_2_ref + '_text_' + numAdd(col_2_list.length + 4)"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>

                    </scroller>

                </div>

                <div class="picker-item" :style="pickerItemStyle">

                    <div class="picker-bar" :style="pickerBarStyle"></div>

                    <scroller class="picker-item-list"
                              show-scrollbar="false"
                              :ref="col_3_ref"
                              scroll-direction="vertical"
                              :style="pickerItemStyle" @scroll="onScroll" @scrollend="e => scrollEnd(e, col_3_ref)">

                        <text @disappear="e => disAppearPickItem(e, col_3_ref, 0)"
                              @appear="e => appearPickItem(e, col_3_ref, 0)"
                              :ref="col_3_ref + '_text_0'"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>
                        <text @disappear="e => disAppearPickItem(e, col_3_ref, 1)"
                              @appear="e => appearPickItem(e, col_3_ref, 1)"
                              :ref="col_3_ref + '_text_1'"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>

                        <text @disappear="e => disAppearPickItem(e, col_3_ref, index + 2)"
                              @appear="e => appearPickItem(e, col_3_ref, index + 2)"
                              :ref="col_3_ref + '_text_' + numAdd(index,2)"
                              v-for="(item, index) of col_3_list"
                              :key="col_3_ref + '_' + index"
                              class="picker-item-text"
                              :style="pickerItemTextStyle">{{ (item.title || '') }}
                        </text>

                        <text @disappear="e => disAppearPickItem(e, col_3_ref, col_3_list.length + 3)"
                              @appear="e => appearPickItem(e, col_3_ref, col_3_list.length + 3)"
                              :ref="col_3_ref + '_text_' + numAdd(col_3_list.length + 3)"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>
                        <text @disappear="e => disAppearPickItem(e, col_3_ref, col_3_list.length + 4)"
                              @appear="e => appearPickItem(e, col_3_ref, col_3_list.length + 4)"
                              :ref="col_3_ref + '_text_' + numAdd(col_3_list.length + 4)"
                              class="picker-item-text"
                              :style="pickerItemTextStyle"></text>

                    </scroller>

                </div>


            </div>

            <div :class="['picker-btn', isipx() ? 'ipx-bottom' : '']">
                <text class="picker-btn-text" @click="change">确定</text>
                <text class="picker-btn-text" @click="cancel">取消</text>
            </div>

        </wxc-popup>

    </div>
</template>

<script>

  const componentWidth = '750'
  const platform = weex.config.env.platform.toLowerCase()
  const defaultPadding = 15;

  import WxcPopup from './wxc-popup';

  import Type from './type'
  import AreaDataSet from './area'

  const dom = weex.requireModule('dom')

  export default {
    name: "x-picker",
    components: {WxcPopup},
    data: () => ({
      showPopup: false,

      pickerWidth: 750,

      pickerHeight: 450,

      pickerBarHeight: 90,

      pickerItemTextHeight: 90,

      column: 3,

      col_1_ref: 'picker_col_1',

      col_2_ref: 'picker_col_2',

      col_3_ref: 'picker_col_3',

      col_1_list: [],

      col_2_list: [],

      col_3_list: [],

      checked_col_1: 0,

      checked_col_2: 0,

      checked_col_3: 0,

      webPickerTimer: null

    }),
    props: {
      // 是否显示 picker
      show: {
        type: Boolean,
        default: false,
      },
      // 类型   signle（单选） area（区域） section(区间) date（日期） time（时间）
      type: {
        type: String,
        default: 'single'
      },
      dataset: {
        type: Array,
        default: ()=>([])
      },
      yearSection: {
        type: Array,
        default: ()=>([1949, new Date().getFullYear()])
      },
      linkageColumn: {
        type: Number,
        default: 2
      },
      defaultTitle:{
        type: String,
        dafault: null
      }
    },
    created() {

      // 初始化列数
      this.changeColumn()

      // 初始化列数据
      this.initColumns()

    },
    computed: {
      pickerItemStyle() {
        var style = {}
        var width = this.pickerWidth / this.column
        style['width'] = width + 'px'
        return style
      },
      pickerItemTextStyle() {
        var style = {}
        var width = this.pickerWidth / this.column
        style['width'] = width + 'px'
        return style
      },
      pickerBarStyle() {
        var style = {}

        var margin = 4
        var width = this.pickerWidth / this.column - (margin * 2)
        var top = this.pickerHeight / 2 - (this.pickerBarHeight / 2)
        style['width'] = width + 'px'
        style['top'] = top + 'px'
        style['height'] = this.pickerBarHeight + 'px'
        style['marginLeft'] = margin + 'px'
        style['marginRight'] = margin + 'px'
        if (this.isWeb())
          style['position'] = 'fixed'
        return style
      }

    },
    methods: {
      numAdd(...num) {
        return num.reduce((ret, item) => {
          ret += item;
          return ret;
        }, 0)
      },
      // 判断 是否是iphonex
      isipx() {
        return weex && (weex.config.env.deviceModel === 'iPhone10,3' || weex.config.env.deviceModel === 'iPhone10,6');
      },
      isWeb() {
        return 'web' === platform
      },
      PopupOverlayClick(e) {
        this.$emit('overlayClick', e)
      },

      changeColumn () {
        var type = this.type;

        if(Type.area === type){
          this.column = 3;
        } else if(Type.section === type){
          this.column = 2;
        } else if(Type.date === type){
          this.column = 3;
        } else if(Type.time === type) {
          this.column = 2;
        } else if(Type.linkage === type){
          this.column = this.linkageColumn;
        } else {
          this.column = 1;
        }

      },
      initColumns () {

        var type = this.type;
        var dataset = this.dataset;

        if(Type.area === type && dataset.length == 0){  // 如果选择了区域，且没有指定数据集时使用默认数据集
          dataset = AreaDataSet;
        }

        if(Type.section === type){
          if(this.column > 0) {
            this.col_1_list = dataset[0]
            this.checked_col_1 = 0
          }
          if(this.column > 1) {
            this.col_2_list = dataset[1]
            this.checked_col_2 = 0
          }

        } else if(Type.date === type){
          if(this.column > 0) {
            this.col_1_list = this.generTimeYear();
            this.checked_col_1 = 0;
          }
          if(this.column > 1) {
            this.col_2_list = this.generTimeMonth()
            this.checked_col_2 = 0;
          }
          if(this.column > 2) {
            this.col_3_list = this.generTimeDate()
            this.checked_col_3 = 0;
          }

        } else if(Type.time === type){
          if(this.column > 0) {
            this.col_1_list = this.generTimeHour()
            this.checked_col_1 = 0
          }
          if(this.column > 1) {
            this.col_2_list = this.generTimeMinute()
            this.checked_col_2 = 0
          }
        } else {
          if(this.column > 0) {
            this.col_1_list = dataset;
            this.checked_col_1 = 0;
          }
          if(this.column > 1) {
            this.col_2_list = this.col_1_list && this.col_1_list[0] && this.col_1_list[0].children || []
            this.checked_col_2 = 0;
          }
          if(this.column > 2) {
            this.col_3_list =  this.col_2_list && this.col_2_list[0] && this.col_2_list[0].children || []
            this.checked_col_3 = 0;
          }
        }

        if(this.defaultTitle){
          this.refreshCheckedByDefaultTitle()
        }

        this.refreshColumns()
      },
      refreshColumns () {
        var _self = this;
        var timer = setTimeout(function(){
          clearTimeout(timer)
          _self.checkedItem(_self.col_1_ref, _self.checked_col_1)
          timer = setTimeout(function(){
            clearTimeout(timer)
            _self.checkedItem(_self.col_2_ref, _self.checked_col_2)
            timer = setTimeout(function(){
              clearTimeout(timer)
              _self.checkedItem(_self.col_3_ref, _self.checked_col_3)
            }, 30)
          }, 15)
        }, 5)
      },
      onScroll(e) {

      },

      scrollEnd(e, ref) {

        console.log('scroll end')
        console.log('current checked', this.checked_col_1)

        var check_col = 0;
        if (this.col_1_ref == ref) {
          check_col = this.checked_col_1
        } else if (this.col_2_ref == ref) {
          check_col = this.checked_col_2
        } else if (this.col_3_ref == ref) {
          check_col = this.checked_col_3
        }

        this.checkedItem(ref, check_col)

        if (this.column > 1) {
          var refarr = ref.split('_')
          var crt_col = parseInt(refarr[2])

          if(!~[Type.time, Type.section].indexOf(this.type)) {
            this.updateOtherCol(crt_col + 1)
          }
        }

      },

      appearPickItem(e, ref, index) {

        if (!e.direction){ return;}

        console.log('appear ', ref, ' ', index, e.direction)

        var checked_index = index + (e.direction == 'down' ? 2 : -2);
        checked_index -= 2
        if (checked_index < 0) {
          checked_index = 0;
        }

        if (this.col_1_ref == ref) {
          this.checked_col_1 = checked_index >= this.col_1_list.length
            ? this.col_1_list.length - 1
            : checked_index
        } else if (this.col_2_ref == ref) {
          this.checked_col_2 = checked_index >= this.col_2_list.length
            ? this.col_2_list.length - 1
            : checked_index
        } else if (this.col_3_ref == ref) {
          this.checked_col_3 = checked_index >= this.col_3_list.length
            ? this.col_3_list.length - 1
            : checked_index
        }

        if(this.isWeb()){
          var _self = this;
          if(this.webPickerTimer){
            clearTimeout(this.webPickerTimer)
          }
          this.webPickerTimer = setTimeout(function(){
            clearTimeout(_self.webPickerTimer)
            _self.webPickerTimer = null
            _self.scrollEnd(e, ref)
          }, 500)
        }
      },

      disAppearPickItem(e, ref, index) {

        if (!e.direction){ return;}

        console.log('disappear ', ref, ' ', index, e.direction)

        var checked_index = index + (e.direction == 'up' ? 3 : -3);
        checked_index -= 2
        if (checked_index < 0) {
          checked_index = 0;
        }

        if (this.col_1_ref == ref) {
          this.checked_col_1 = checked_index >= this.col_1_list.length
            ? this.col_1_list.length - 1
            : checked_index
        } else if (this.col_2_ref == ref) {
          this.checked_col_2 = checked_index >= this.col_2_list.length
            ? this.col_2_list.length - 1
            : checked_index
        } else if (this.col_3_ref == ref) {
          this.checked_col_3 = checked_index >= this.col_3_list.length
            ? this.col_3_list.length - 1
            : checked_index
        }

        if(this.isWeb()){
          var _self = this;

          if(this.webPickerTimer){
            clearTimeout(this.webPickerTimer)
          }
          this.webPickerTimer = setTimeout(function(){
            clearTimeout(_self.webPickerTimer)
            _self.webPickerTimer = null
            _self.scrollEnd(e, ref)
          }, 500)
        }
      },

      // 更新其他列
      updateOtherCol(col) {

        var col_ref = null;

        if(Type.date === this.type) {
          if (col == 2) {
            col_ref = this.col_2_ref
            this.col_2_list = this.generTimeMonth();
            this.checked_col_2 = 0;
          } else if (col == 3) {
            col_ref = this.col_3_ref
            this.col_3_list =  this.generTimeDate();
            this.checked_col_3 = 0;
          }
        } else {
          if (col == 2) {
            col_ref = this.col_2_ref
            var prt_item = this.col_1_list[this.checked_col_1] || {}
            this.col_2_list = 'children' in prt_item ? prt_item.children : [];
            this.checked_col_2 = 0;
          } else if (col == 3) {
            col_ref = this.col_3_ref
            var prt_item = this.col_2_list[this.checked_col_2] || {}
            this.col_3_list = 'children' in prt_item ? prt_item.children : [];
            this.checked_col_3 = 0;
          }
        }
        if (col_ref) {
          this.checkedItem(col_ref, 0)

          if (this.column > col) {
            this.updateOtherCol(col + 1)
          }
        }
      },

      // 选择 某列 某项
      checkedItem(ref, idx) {
        var scrollToItem = null;
        if(!ref) return;

        scrollToItem = this.$refs[ref + '_text_' + idx]

        if (scrollToItem) {
          scrollToItem = Array.isArray(scrollToItem)
            ? scrollToItem.length > 0 ? scrollToItem[0] : null
            : scrollToItem;
          if (scrollToItem) {
            dom.scrollToElement(scrollToItem, {animated: true})
          }
        }
      },

      generTimeYear () {
        var yearSection = this.yearSection
        var maxYear = Math.max(...yearSection) || new Date().getFullYear()
        var minYear = Math.min(...yearSection) || 1949
        var dataset = Array.from({length: maxYear - minYear + 1}).map((item,index)=>{return {
          title: maxYear - index + '',
          value: maxYear - index
        }})
        return dataset;
      },
      generTimeMonth () {
        var dataset = Array.from({length: 12}).map((item,index)=>{return {
          title: (index+1) > 9 ? (index + 1 + '') : ('0'+(index + 1)),
          value: index + 1
        }})
        return dataset;
      },
      generTimeDate () {
        var result = this.getResult()
        var values = result.values
        var year = values[0]
        var month = values[1]
        var dateCount = new Date(year, month, 0).getDate();
        var dataset = Array.from({length: dateCount}).map((item,index)=>{return {
          title: (index+1) > 9 ? (index + 1 + '') : ('0'+(index + 1)),
          value: index + 1
        }})
        return dataset;
      },

      generTimeHour (){
        var dataset = Array.from({length: 24}).map((item,index)=>{return {
          title: index > 9 ? ('' + index) : ('0'+index),
          value: index
        }})
        return dataset;
      },

      generTimeMinute () {
        var dataset = Array.from({length: 60}).map((item,index)=>{return {
          title: index > 9 ? ('' + index) : ('0'+index),
          value: index
        }})
        return dataset;
      },

      findItemByTitle (ref, title){
        var arr = null
        if(this.col_1_ref == ref){
          arr = this.col_1_list
        } else if(this.col_2_ref == ref){
          arr = this.col_2_list
        } else if(this.col_3_ref == ref) {
          arr = this.col_3_list
        }
        return this.findIndexByTitle(arr, title)
      },

      findIndexByTitle (arr, t){
        var idx = -1;
        if(!arr){ return idx; }
        console.log('find index title ,arr length :', arr.length)
        for(var i = 0; i < arr.length; i++){
          var item = arr[i]
          var title = item.title
          if(t === title){
            idx = i;
            break;
          }
        }
        return idx;
      },

      getResult(){
        var rst = {};
        var titles = [];
        var values = [];
        var checked = [];

        if (this.col_1_list.length > 0) {
          if (this.checked_col_1 >= 0
            && this.checked_col_1 < this.col_1_list.length
            && this.col_1_list[this.checked_col_1]) {
            var checkobj = Object.assign({}, this.col_1_list[this.checked_col_1] || {});
            var title = 'title' in checkobj ? checkobj.title : ''
            var value = 'value' in checkobj ? checkobj.value : title
            titles.push(title);
            values.push(value);
            checkobj.children && delete checkobj.children;
            checked.push(checkobj);
          } else {
            titles.push(null);
            values.push(null);
            checked.push(null);
          }
        } else {
          titles.push(null);
          values.push(null);
          checked.push(null);
        }

        if(this.column > 1) {
          if (this.col_2_list.length > 0) {
            if (this.checked_col_2 >= 0
              && this.checked_col_2 < this.col_2_list.length
              && this.col_2_list[this.checked_col_2]) {
              var checkobj = Object.assign({}, this.col_2_list[this.checked_col_2] || {});
              var title = 'title' in checkobj ? checkobj.title : ''
              var value = 'value' in checkobj ? checkobj.value : title
              titles.push(title);
              values.push(value);
              checkobj.children && delete checkobj.children;
              checked.push(checkobj);
            } else {
              titles.push(null);
              values.push(null);
              checked.push(null);
            }
          } else {
            titles.push(null);
            values.push(null);
            checked.push(null);
          }
        }

        if(this.column　> 2) {
          if (this.col_3_list.length > 0) {
            if (this.checked_col_3 >= 0
              && this.checked_col_3 < this.col_3_list.length
              && this.col_3_list[this.checked_col_3]) {
              var checkobj = Object.assign({}, this.col_3_list[this.checked_col_3] || {});
              var title = 'title' in checkobj ? checkobj.title : ''
              var value = 'value' in checkobj ? checkobj.value : title
              titles.push(title);
              values.push(value);
              checkobj.children && delete checkobj.children;
              checked.push(checkobj);
            } else {
              titles.push(null);
              values.push(null);
              checked.push(null);
            }
          } else {
            titles.push(null);
            values.push(null);
            checked.push(null);
          }
        }
        rst['titles'] = titles;
        rst['values'] = values;
        rst['title'] = titles.join(' ');
        rst['value'] = values.join(' ');
        rst['checked'] = checked;
        return rst;
      },

      // 当点击确定时
      change(e) {

        var event = this.getResult()

        this.$emit('onchange', event);

        this.cancel(e);
      },
      cancel (e) {
        this.PopupOverlayClick(e)
      },

      refreshCheckedByDefaultTitle () {
        var defaultTitle = this.defaultTitle || ''

        var arr = defaultTitle.split(' ')
        if(arr.length > 0) {
          this.checked_col_1 = this.findItemByTitle(this.col_1_ref, arr[0])
          this.checked_col_1 = this.checked_col_1 < 0 ? 0 : this.checked_col_1
        }
        if(arr.length > 1) {
          this.checked_col_2 = this.findItemByTitle(this.col_2_ref, arr[1])
          this.checked_col_2 = this.checked_col_2 < 0 ? 0 : this.checked_col_2
        }
        if(arr.length > 2) {
          this.checked_col_3 = this.findItemByTitle(this.col_3_ref, arr[2])
          this.checked_col_3 = this.checked_col_3 < 0 ? 0 : this.checked_col_3
        }
      }
    },
    watch: {
      show (crt) {
        if(crt) {
          this.refreshCheckedByDefaultTitle()
          this.refreshColumns()
        }
      },

      type () {
        this.changeColumn()
        this.initColumns()
      },

      dataset (crt) {
        if(!crt) this.dataset = [];
        this.changeColumn()
        this.initColumns()
      },

      linkageColumn (crt) {
        this.column = crt
      },

      defaultTitle (crt, old){
        if(crt == old) return;
        this.refreshCheckedByDefaultTitle()
        this.refreshColumns()
      }
    }
  };
</script>

<style scoped>

    .picker {
        position: absolute;
        left: 0px;
        top: 0px;
        width: 750px;
        flex: 1;
    }

    .picker-content {
        width: 750px;
        height: 450px;
        flex-direction: row;
    }

    .picker-btn {
        width: 750px;
        height: 100px;
        /*margin-bottom: 30px;*/
        text-align: right;
        flex-direction: row-reverse;
    }

    .picker-btn-text {
        color: #FA4D50;
        font-size: 32px;
        margin-right: 40px;
        line-height: 100px;
    }

    .picker-item {
        position: relative;
        top: 0px;
        height: 450px;
        padding-left: 0px;
        padding-right: 0px;
        padding-top: 0px;
        padding-bottom: 0px;
        overflow-x: hidden;
        overflow-y: scroll;
    }

    .picker-item-list {
        height: 448px; /* 在原来height上减少2px，解决iphone滑到最上面选择了第二个的问题 */
        padding-left: 4px;
        padding-right: 4px;
    }

    .picker-item-text {
        height: 90px;
        line-height: 90px;
        font-size: 40px;
        text-align: center;
        word-wrap: normal;
        white-space: nowrap;
    }

    .picker-bar {
        position: absolute;
        top: auto;
        border-top-width: 4px;
        border-top-style: solid;
        border-top-color: #FA4D50;
        border-bottom-width: 4px;
        border-bottom-style: solid;
        border-bottom-color: #FA4D50;
    }

    .ipx-bottom {
        padding-bottom: 30px;
    }

</style>
