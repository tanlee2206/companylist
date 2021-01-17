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
        <tr v-for="cpn in company" :key="company._id">
          <th scope="row">
            {{ cpn._id }}
          </th>
          <td>{{ cpn.name }}</td>
          <td><span class="badge badge-info">on</span></td>
          <td>22/11/2020</td>
          <td>22/11/2021</td>
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

  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  asyncData (context) {
    return new Promise((resolve, reject) => {
      // eslint-disable-next-line nuxt/no-timing-in-fetch-data
      setTimeout(() => {
        resolve({
          company: [
            {
              _id: 1,
              name: 'TBV',
              status: 1
            },
            {
              name: 'DEK',
              _id: 2,
              status: 1
            },
            {
              _id: 3,
              name: 'TMA',
              status: 1
            },
            {
              _id: 4,
              name: 'FPT',
              status: 1
            },
            {
              _id: 5,
              name: 'VNPT',
              status: 1
            }

          ]
        })
      }, 2000)
    }).then((data) => {
      // console.log(data)
      return data
    }).catch((e) => {
      console.log(e)
    })
  }

}
</script>
