<template>
<div>
  <BrowseDemo v-if="isShowBrowseDemo" />
  <el-container>
    <el-main>
      <el-table
        :data="tableData.filter(data => !search || data.name.toLowerCase().includes(search.toLowerCase()))"
        style="width: 100%">
        <el-table-column
          label="ProjectName"
          prop="projectName"
          width="250">
        </el-table-column>
        <el-table-column
          label="Describe"
          prop="describe">
        </el-table-column>
        <el-table-column
          label="Person"
          prop="person"
          width="150">
        </el-table-column>
        <el-table-column
          label="Date"
          prop="date"
          width="150">
        </el-table-column>
        <el-table-column
          label="Version"
          prop="version"
          width="150">
        </el-table-column>
        <el-table-column
          align="right"
          width="350">
          <template slot="header">
            <el-input
              v-model="search"
              size="mini"
              placeholder="输入关键字搜索"/>
          </template>
          <template>
            <el-button
              size="mini"
              @click="handleDownload(1, 1)">Download</el-button>
            <el-button
              size="mini"
              @click="handleBrowse(1, 1)">Perview</el-button>
            <el-button
              size="mini"
              @click="handleEdit(2, 2)">Edit</el-button>
            <el-button
              size="mini"
              type="danger"
              @click="handleDelete(scope.$index, scope.row)">Delete</el-button>
          </template>
        </el-table-column>
      </el-table>
      <BrowseDemo v-bind:browseVisible="isShowBrowseDemo" @close-browse="handleCloseBrowse($event)"/>
      <AddProject v-bind:dialogFormVisible="isShowAddProject" @close-browse="handleCloseAddProject($event)"/>
    </el-main>

    <el-footer style="height: 40px;">
      <Paging/>
    </el-footer>
</el-container>
  </div>
</template>

<script>
  import Paging from './Paging'
  import BrowseDemo from './BrowseDemo'
  import AddProject from './AddProject'

  export default {
    data() {
      return {
        tableData: [{
          date: '2016-05-02',
          projectName: '摸鱼儿·雁丘辞',
          describe: '天南地北双飞客，老翅几回寒暑。',
          person: '元好问',
          version: '5.1.0'
        }, {
          date: '2016-05-02',
          projectName: '花非花',
          describe: '花非花，雾非雾。夜半来，天明去。来如春梦几多时?去似朝云无觅处。',
          person: '白居易',
          version: '5.1.0'
        }, {
          date: '2016-05-02',
          projectName: '诗词大会',
          describe: '古人学问无遗力，少壮工夫老始成。纸上得来终觉浅，绝知此事要躬行。',
          person: '陆游',
          version: '5.1.0'
        }, {
          date: '2016-05-02',
          projectName: '赵毅',
          describe: '李杜诗篇万口传，至今已觉不新鲜。江山代有才人出，各领风骚数百年。',
          person: '赵毅',
          version: '5.1.0'
        }, {
          date: '2016-05-02',
          projectName: '浪淘沙',
          describe: '借问江潮与海水，何似君情与妾心。相恨不如潮有信，相思始觉海非深。',
          person: '白居易',
          version: '5.1.0'
        }, {
          date: '2016-05-02',
          projectName: '玉楼春',
          describe: '尊前拟把归期说。未语春容先惨咽。人生自是有情痴，此恨不关风与月。',
          person: '欧阳修',
          version: '5.1.0'
        }, {
          date: '2016-05-02',
          projectName: '花月痕·第十五回诗',
          describe: '多情自古空余恨，好梦由来最易醒。',
          person: '魏子安',
          version: '5.1.0'
        }],
        search: '',
        key: 0,
        isShowBrowseDemo: false,
        isShowAddProject: false
      }
    },
    components: {
      Paging,
      BrowseDemo,
      AddProject
    },
    methods: {
      handleEdit(index, row) {
        console.log(index, row);
        this.isShowAddProject = true
      },
      handleDelete(index, row) {
        console.log(index, row);
      },
      handleBrowse(index, row) {
        this.isShowBrowseDemo = true;
        console.log(index, row);
      },
      handleCloseBrowse(param) {
        console.log(param);
        this.isShowBrowseDemo = false;
      },
      handleCloseAddProject(param) {
        console.log(param);
        this.isShowAddProject = false;
      }
    },
    computed: {}
  }
</script>