<template>
  <section class="create">
    <hr />
    <el-input type="text" v-model="title" placeholder="Title" />
    <br />
    <br />
    <el-input
      class="memo"
      type="textarea"
      :autosize="autosize"
      v-model="memo"
      placeholder="Memo"
    />
    <br />
    <br />
    <el-button :disabled="noText" class="btn" type="danger" @click="clearText">
      <div class="el-icon-delete"></div>
    </el-button>
    <el-button :disabled="noText" class="btn" type="success" @click="logData">
      <div class="el-icon-folder-checked"></div>
    </el-button>
    <hr />

    <h4>Debug</h4>
    <code>
      <pre class="code">{{ activeNote }}</pre>
    </code>
    Lines: {{ lines }}<br />
    Length: {{ memo.length }}
    <div class="img"></div>
  </section>
</template>

<script>
  import moment from 'moment';
  import { v4 as uuidv4 } from 'uuid';
  export default {
    name: 'Create',
    data() {
      return {
        title: '',
        memo: '',
        lineCount: 0,
      };
    },
    methods: {
      clearText() {
        this.title = '';
        this.memo = '';
      },
      logData() {
        alert(this.memo);
      },
      saveNote() {
        alert('save');
      },
      countLines(value) {
        return value.split(/\r?\n/g)?.length || 0;
      },
    },
    computed: {
      noText() {
        return this.title?.length + this.memo?.length === 0;
      },
      lines() {
        return this.countLines(this.memo) + this.memo?.length / 33;
      },
      autosize() {
        return this.lines > 2;
      },
      activeNote() {
        return {
          id: uuidv4(),
          title: this.title,
          memo: this.memo,
          timestamp: moment().toString(),
        };
      },
    },
  };
</script>

<style scoped>
  a {
    text-decoration: none;
    color: currentColor;
  }

  .code {
    border-radius: 0.3rem;
    padding: 10px;
    background-color: black;
    white-space: pre-wrap;
    text-align: left;
  }

  .btn {
    font-size: 1.2rem;
  }

  .memo {
    width: 100%;
  }

  .btn-small {
    padding: 0.5rem;
    margin: auto;
    font-size: 0.7rem;
    border-radius: 0.25rem;
  }

  .img {
    background: url('data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiA/PjxzdmcgaGVpZ2h0PSIyNCIgdmVyc2lvbj0iMS4xIiB3aWR0aD0iMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6Y2M9Imh0dHA6Ly9jcmVhdGl2ZWNvbW1vbnMub3JnL25zIyIgeG1sbnM6ZGM9Imh0dHA6Ly9wdXJsLm9yZy9kYy9lbGVtZW50cy8xLjEvIiB4bWxuczpyZGY9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkvMDIvMjItcmRmLXN5bnRheC1ucyMiPjxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAgLTEwMjguNCkiPjxwYXRoIGQ9Im01IDEwMzAuNGMtMS4xMDQ2IDAtMiAwLjktMiAydjggNCA2YzAgMS4xIDAuODk1NCAyIDIgMmgxNGMxLjEwNSAwIDItMC45IDItMnYtNi00LTQtNGMwLTEuMS0wLjg5NS0yLTItMmgtNC0xMHoiIGZpbGw9IiNiZGMzYzciLz48ZyBmaWxsPSIjOTVhNWE2Ij48cGF0aCBkPSJtNiAxMDI4LjRjLTAuNTUyMyAwLTEgMC40LTEgMXYzYzAgMC41IDAuNDQ3NyAxIDEgMXMxLTAuNSAxLTF2LTNjMC0wLjYtMC40NDc3LTEtMS0xem00IDBjLTAuNTUyMyAwLTEgMC40LTEgMXYzYzAgMC41IDAuNDQ3NyAxIDEgMSAwLjU1MiAwIDEtMC41IDEtMXYtM2MwLTAuNi0wLjQ0OC0xLTEtMXptNCAwYy0wLjU1MiAwLTEgMC40LTEgMXYzYzAgMC41IDAuNDQ4IDEgMSAxczEtMC41IDEtMXYtM2MwLTAuNi0wLjQ0OC0xLTEtMXptNCAwYy0wLjU1MiAwLTEgMC40LTEgMXYzYzAgMC41IDAuNDQ4IDEgMSAxczEtMC41IDEtMXYtM2MwLTAuNi0wLjQ0OC0xLTEtMXoiLz48cmVjdCBoZWlnaHQ9IjEiIHdpZHRoPSIxMiIgeD0iNiIgeT0iMTA0My40Ii8+PHJlY3QgaGVpZ2h0PSIxIiB3aWR0aD0iMTIiIHg9IjYiIHk9IjEwNDAuNCIvPjxyZWN0IGhlaWdodD0iMSIgd2lkdGg9IjEyIiB4PSI2IiB5PSIxMDM3LjQiLz48cmVjdCBoZWlnaHQ9IjEiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAgMTAyOC40KSIgd2lkdGg9IjQiIHg9IjYiIHk9IjE4Ii8+PC9nPjxwYXRoIGQ9Im01IDEwMzIuNGMwIDAuNSAwLjQ0NzcgMSAxIDFzMS0wLjUgMS0xaC0yem00IDBjMCAwLjUgMC40NDc3IDEgMSAxIDAuNTUyIDAgMS0wLjUgMS0xaC0yem00IDBjMCAwLjUgMC40NDggMSAxIDFzMS0wLjUgMS0xaC0yem00IDBjMCAwLjUgMC40NDggMSAxIDFzMS0wLjUgMS0xaC0yeiIgZmlsbD0iIzdmOGM4ZCIvPjxwYXRoIGQ9Im0zIDEwNDkuNHYxYzAgMS4xIDAuODk1NCAyIDIgMmgxNGMxLjEwNSAwIDItMC45IDItMnYtMWMwIDEuMS0wLjg5NSAyLTIgMmgtMTRjLTEuMTA0NiAwLTItMC45LTItMnoiIGZpbGw9IiM5NWE1YTYiLz48ZyB0cmFuc2Zvcm09Im1hdHJpeCguNzA3MTEgLjcwNzExIC0uNzA3MTEgLjcwNzExIDc3My4yMiAzNzAuNCkiPjxwYXRoIGQ9Im0tNjMgMTAwMy40djExLjMgMC43IDFsMiAyIDItMnYtMS0wLjctMTEuM2gtNHoiIGZpbGw9IiNlY2YwZjEiLz48cGF0aCBkPSJtLTYxIDEwMDMuNHYxNWwyLTJ2LTEtMC43LTExLjNoLTJ6IiBmaWxsPSIjYmRjM2M3Ii8+PHJlY3QgZmlsbD0iI2U2N2UyMiIgaGVpZ2h0PSIxMSIgd2lkdGg9IjQiIHg9Ii02MyIgeT0iMTAwNC40Ii8+PHBhdGggZD0ibS02MSAxMDAwLjRjLTEuMTA1IDAtMiAwLjktMiAydjFoNHYtMWMwLTEuMS0wLjg5NS0yLTItMnoiIGZpbGw9IiM3ZjhjOGQiLz48ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgtNywxKSI+PHBhdGggZD0ibS01NS40MDYgMTAxNiAxLjQwNiAxLjQgMS40MDYtMS40aC0xLjQwNi0xLjQwNnoiIGZpbGw9IiMzNDQ5NWUiLz48cGF0aCBkPSJtLTU0IDEwMTZ2MS40bDEuNDA2LTEuNGgtMS40MDZ6IiBmaWxsPSIjMmMzZTUwIi8+PC9nPjxwYXRoIGQ9Im0tNjEgMTAwMC40Yy0xLjEwNSAwLTIgMC45LTIgMnYxaDJ2LTN6IiBmaWxsPSIjOTVhNWE2Ii8+PHJlY3QgZmlsbD0iI2QzNTQwMCIgaGVpZ2h0PSIxMSIgd2lkdGg9IjIiIHg9Ii02MSIgeT0iMTAwNC40Ii8+PC9nPjwvZz48L3N2Zz4=');
  }
</style>
