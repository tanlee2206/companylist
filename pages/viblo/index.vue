<template>
  <div>
    <button type="button" class="btn btn-primary btn-lg mb-4 mt-4" data-toggle="modal" data-target="#ModalLoginForm">
      Launch demo modal
    </button>
    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th scope="col">
            #
          </th>
          <th scope="col">
            Name
          </th>
          <th scope="col">
            Status
          </th>
          <th scope="col">
            Updated_at
          </th>
          <th scope="col">
            Create_at
          </th>
          <th>
            Edit
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="pos in postv" :key="postv.id">
          <th scope="row">
            {{ pos.id }}
          </th>
          <td>{{ pos.name }}</td>
          <td><span class="badge badge-info">on</span></td>
          <td>{{ pos.created_at }}</td>
          <td>{{ pos.updated_at }}</td>
          <td>
            <button class="btn btn-success">
              Edit
            </button>
          </td>
        </tr>
      </tbody>
    </table>
    <!-- Modal HTML Markup -->
    <div id="ModalLoginForm" class="modal fade">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header" />
          <div class="modal-body">
            <h1>Create!</h1>
            <form role="form" method="POST" action="">
              <input type="hidden" name="_token" value="">
              <div class="form-group">
                <label class="control-label">Name</label>
                <div>
                  <input type="text" class="form-control input-lg" name="name" value="">
                </div>
              </div>
              <div class="form-group">
                <label class="control-label">Status</label>
                <div>
                  <select id="sel1" class="form-control">
                    <option>1</option>
                    <option>2</option>
                    <option>3</option>
                    <option>4</option>
                  </select>
                </div>
              </div>
              <div class="form-group">
                <div>
                  <button type="submit" class="btn btn-success">
                    save
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div><!-- /.modal-content -->
      </div><!-- /.modal-dialog -->
    </div><!-- /.modal -->
  </div>
</template>

<script>

export default {
  async asyncData ({ $axios }) {
    const api = 'http://[::1]:3000/company2s?filter=%7B%0A%20%20%22offset%22%3A%200%2C%0A%20%20%22limit%22%3A%20100%2C%0A%20%20%22skip%22%3A%200%2C%0A%20%20%22where%22%3A%20%7B%0A%20%20%20%20%22additionalProp1%22%3A%20%7B%7D%0A%20%20%7D%2C%0A%20%20%22fields%22%3A%20%7B%0A%20%20%20%20%22id%22%3A%20true%2C%0A%20%20%20%20%22name%22%3A%20true%2C%0A%20%20%20%20%22status%22%3A%20true%2C%0A%20%20%20%20%22created_at%22%3A%20true%2C%0A%20%20%20%20%22updated_at%22%3A%20true%0A%20%20%7D%0A%7D'
    const postv = await $axios.$get(api).then((response)=>{
      return response
    })
    console.log(postv);
    return { postv }
  }
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  // async fetch () {
  //   this.postv = await fetch(
  //     'https://viblo.asia/api/posts?limit=10'
  //   ).then(res => res.json())
  // },

  // data () {
  //   return {
  //     postv: []
  //   }
  // }

}
</script>
