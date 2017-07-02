<template>
  <section class="container">
    <div class="tag__filter">
      <el-select class="tag__select" v-model="tags" multiple placeholder="请选择标签">
        <el-option v-for="tag in htmlTags" :key="tag" :label="tag" :value="tag"></el-option>
      </el-select>
      <el-input placeholder="请输入属性" class="tag__property" type="text" v-model="property"></el-input>    
    </div>
    <el-card class="result">
      <ul class="tag-list">
        <li v-for="defaultValue in defaultValues" :key="defaultValue.tag">
          <label class="tag__label">{{defaultValue.tag}}:</label>
          <span class="tag__value">{{defaultValue.value}}</span>
        </li>
      </ul>
    </el-card>
  </section>
</template>

<script>
import { htmlTags } from '../data'
import { Select, Option, Input, Card } from 'element-ui'
export default {
  head () {
    return {
      title: '浏览器默认属性获取'
    }
  },
  data () {
    return {
      property: '',
      htmlTags,
      tags: []
    }
  },
  components: {
    ElSelect: Select,
    ElOption: Option,
    ElInput: Input,
    ElCard: Card
  },
  computed: {
    defaultValues: {
      get () {
        if (process.BROWSER_BUILD) {
          const htmlTags = this.tags.length > 0 ? this.tags : this.htmlTags
          return htmlTags.map(tag => {
            const element = document.createElement(tag)
            switch (tag) {
              case 'a':
                element.href = 'https://github.com'
            }
            document.body.appendChild(element)
            const value = getComputedStyle(element, '').getPropertyValue(this.property)
            element.parentNode.removeChild(element)
            return {
              tag,
              value
            }
          })
        }
        return []
      }
    }
  }
}
</script>

<style scoped>
  .tag__filter {
    display: flex;
    width: 100%;
  }
  .tag__select {
    width: 100%;
  }
  .tag__property {
    margin-left: 20px;
  } 
  .result {
    margin-top: 20px;
  }
  .tag-list,
  .tag-list li {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  .tag-list li {
    display: flex;
  }
  .tag__label {
    width: 100px;
    text-align: right;
  }
  .tag__value {
    flex: 1;
    padding-left: 20px;
    color: #1D8CE0;
  }
</style>
