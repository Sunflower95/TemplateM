<template>
    <div class="container">
       <div class="row-mt-5">
          <div class="col-md-12">
            <div class="card">
              <div class="card-header">
                <h3 class="card-title">Users Table</h3>

                <div class="card-tools">
                 <button class="btn btn-success" data-toggle="modal" data-target="#addNew">Add New
                     <i class="fas fa-user-plus fa-fw">

                     </i>
                 </button>
                </div>
              </div>
              <!-- /.card-header -->
              <div class="card-body table-responsive p-0">
                <table class="table table-hover text-nowrap">
                    <tr>
                      <th>ID</th>
                      <th>Name</th>
                      <th>Email</th>
                      <th>Status</th>
                      <th>Registered At</th>
                      <th>Modify</th>
                    </tr>
            
                  <tbody>
                    <tr v-for='user in users' :key='user.id'>
                      <td>{{user.id }}</td>
                      <td>{{user.name | capitalize}}</td>
                       <td>{{user.email | capitalize}}</td>
                       <td>{{user.type | capitalize}}</td>
                        <td>{{user.created_at | myDate}}</td>
                      <td><span class="tag tag-success">Approved</span></td>
                      <td>
                          <a href='#'>
                              <i class='fas fa-edit blue'></i>
                          </a>
                           /
                          <a href='#'>
                              <i class='fas fa-trash red'></i>
                          </a>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
              <!-- /.card-body -->
            </div>
            <!-- /.card -->
          </div>
        </div>
        <div class="modal fade" id="addNew" data-backdrop="static" tabindex="-1" role="dialog" aria-labelledby="addNewLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="addNewLabel">Add New</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
                </button>
            </div>

            <form :submit="createUser">
            <div class="modal-body">
              
                <div class="form-group">
            
                <input v-model="form.name" type="text" name="name" placeholder="Enter your Fullname"
                  class="form-control" :class="{ 'is-invalid': form.errors.has('username') }">
                <has-error :form="form" field="name"></has-error>
              </div>
                <div class="form-group">
     
                  <input v-model="form.email" type="email" name="email" placeholder="Email@gmail.com"
                    class="form-control" :class="{ 'is-invalid': form.errors.has('email') }">
                  <has-error :form="form" field="email"></has-error>
            </div>
           
                    <div class="form-group">
                        <select name="type" v-model="form.type" id="type" class="form-control" :class="{ 'is-invalid': form.errors.has('type') }">
                            <option value="">Select User Role</option>
                            <option value="admin">Admin</option>
                            <option value="user">Standard User</option>
                            <option value="author">Author</option>
                        </select>
                        <has-error :form="form" field="type"></has-error>
                    </div>
              <div class="form-group">
                
                <input v-model="form.bio" type="textarea" name="bio" placeholder="Bio"
                  class="form-control" :class="{ 'is-invalid': form.errors.has('bio') }">
                <has-error :form="form" field="bio"></has-error>
              </div>
              <div class="form-group">
                
                <input v-model="form.password" type="password" name="password" placeholder="Password"
                  class="form-control" :class="{ 'is-invalid': form.errors.has('password') }">
                <has-error :form="form" field="password"></has-error>
              </div>

             
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-danger" data-dismiss="modal">Close</button>
                <button type="submit" class="btn btn-primary">Create</button>
         </div>
        </form>

         
    </div>
  </div>
</div>
    </div>
</template>

<script>
    export default {
      data(){
        return{
          users:{},
        form: new Form({
        name: '',
        email: '',
        type:'',
        bio:'',
        photo:'',
        password: '',
      })
        }
      },
      methods:{
        // loadUsers(){
        //   axios.get('api/user').then(({data})=>(this.users = data.data))
        // },
          createUser(){
            console.log('working');
            // this.$Progress.start();
            // this.form.post('api/user') 
             
                   
            //   this.$Progress.finish();
          }

      },
      
        // created() {
        //     this.loadUsers()
        // }
    }
</script>
