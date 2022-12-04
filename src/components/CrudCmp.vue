<template>
    <div class="data">
        <table class="table table-bordered border-primary">
            <thead>
                <tr>
                    <!-- <th scope="col">Id</th> -->
                    <th scope="col">Name</th>
                    <th scope="col">Email</th>
                    <th scope="col">Number</th>
                    <th scope="col">Website</th>
                    <th scope="col">Street</th>
                    <th scope="col">Suite</th>
                    <th scope="col">Zip Code</th>
                    <th scope="col">Edit</th>
                    <th scope="col">Delete</th>
                    <!-- <th scope="col">Add Record</th> -->
                </tr>
            </thead>
            <tbody>
                <tr v-for="data in items" :key="data.id">
                    <!-- <th scope="row">{{ data.id }}</th> -->
                    <td>{{ data.name }}</td>
                    <td>{{ data.email }}</td>
                    <td>{{ data.phone }}</td>
                    <td>{{ data.website }}</td>
                    <td>{{ data.address.street }}</td>
                    <td>{{ data.address.suite }}</td>
                    <td>{{ data.address.zipcode }}</td>

                    <td>
                        <button type="button" class="btn btn-outline-primary" data-toggle="modal"
                            :data-target="'#myModal' + data.id">
                            <i class="bi bi-pencil-square"></i>
                            Edit</button>
                    </td>
                    <td>
                        <button type="button" class="btn btn-outline-danger" v-on:click="deleteData(data)">
                            <i class="bi bi-trash"></i>
                            Delete
                        </button>

                    </td>
                    <!-- <td>
                       
                    </td> -->

                    <!-- Bootstrap Model in tr starts here -->
                    <div class="modal" tabindex="-1" :id="'myModal' + data.id">
                        <div class="modal-dialog  modal-dialog-centered">
                            <div class="modal-content">
                                <div class="modal-header">
                                    <h5 class="modal-title">Update Information</h5>
                                    <button type="button" class="btn-close" data-dismiss="modal"
                                        aria-label="Close"></button>
                                </div>
                                <!-- Content goes here -->
                                <div class="modal-body">
                                    <form class="row g-3">
                                        <div class="col-md-6">
                                            <label for="name" class="form-label">Name</label>
                                            <input type="name" class="form-control" id="name" v-model="data.name">
                                        </div>
                                        <div class="col-md-6">
                                            <label for="inputEmail4" class="form-label">Email</label>
                                            <input type="email" class="form-control" id="inputEmail4"
                                                v-model="data.email">
                                        </div>
                                        <div class="col-md-6">
                                            <label for="number" class="form-label">Phone Number</label>
                                            <input type="text" class="form-control" id="number" v-model="data.phone">
                                        </div>
                                        <div class="col-md-6">
                                            <label for="number" class="form-label">Website</label>
                                            <input type="text" class="form-control" id="website" v-model="data.website">
                                        </div>
                                        <div class="col-md-6">
                                            <label for="inputZip" class="form-label">Suite</label>
                                            <input type="text" class="form-control" id="suite"
                                                v-model="data.address.suite">
                                        </div>

                                        <div class="col-md-6">
                                            <label for="street" class="form-label">Street</label>
                                            <input type="text" class="form-control" id="street"
                                                v-model="data.address.street">
                                        </div>

                                        <div class=" col-md-6">
                                            <label for="zip" class="form-label">Zip Code</label>
                                            <input type="text" class="form-control" id="zipcode"
                                                v-model="data.address.zipcode">
                                        </div>

                                    </form>

                                </div>
                                <div class="modal-footer">
                                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                                    <button type="button" class="btn btn-primary" v-on:click="updateData(data)"
                                        data-dismiss="modal">Save
                                        changes
                                    </button>
                                    <!-- New Record -->

                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Bootstrap Model in tr ends here -->


                </tr>
            </tbody>
        </table>

    </div>

    <!-- Bootstrap Model in tr starts here -->
    <div class="modal" tabindex="-1" id="Modal">
        <div class="modal-dialog  modal-dialog-centered">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">Update Information</h5>
                    <button type="button" class="btn-close" data-dismiss="modal" aria-label="Close"></button>
                </div>
                <!-- Content goes here -->
                <div class="modal-body">
                    <form class="row g-3">
                        <div class="col-md-6">
                            <label for="name" class="form-label">Name</label>
                            <input type="name" class="form-control" id="name" v-model="this.name">
                        </div>
                        <div class="col-md-6">
                            <label for="inputEmail4" class="form-label">Email</label>
                            <input type="email" class="form-control" id="inputEmail4" v-model="this.email">
                        </div>
                        <div class="col-md-6">
                            <label for="number" class="form-label">Phone Number</label>
                            <input type="text" class="form-control" id="number" v-model="this.phone">
                        </div>
                        <div class="col-md-6">
                            <label for="number" class="form-label">Website</label>
                            <input type="text" class="form-control" id="website" v-model="this.website">
                        </div>
                        <div class="col-md-6">
                            <label for="inputZip" class="form-label">Suite</label>
                            <input type="text" class="form-control" id="suite" v-model="this.suite">
                        </div>

                        <div class="col-md-6">
                            <label for="street" class="form-label">Street</label>
                            <input type="text" class="form-control" id="street" v-model="this.street">
                        </div>

                        <div class=" col-md-6">
                            <label for="zip" class="form-label">Zip Code</label>
                            <input type="text" class="form-control" id="zipcode" v-model="this.zipcode">
                        </div>

                    </form>

                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                    <button type="button" class="btn btn-primary" v-on:click="addNewRecord()" data-dismiss="modal">Save
                        New Record
                    </button>


                </div>
            </div>
        </div>
    </div>

    <!-- Bootstrap Model in tr ends here -->

    <!-- Model for adding new Record -->
    <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#Modal">
        <i class="bi bi-pencil-fill"></i>
        Add Record
    </button>

</template>

<script>
// import Vue from 'vue';

import axios from 'axios';
// import VueAxios from 'vue-axios';
// Vue.use(VueAxios, axios);


export default {
    name: 'CrudCmp',
    data() {
        return {
            items: undefined,
            name: undefined,
            email: undefined,
            street: undefined,
            suite: undefined,
            zipcode: undefined,
            phone: undefined,
            website: undefined,
        }
    },
    methods: {
        // Fetch Data Start
        async getData() {
            await axios.get('http://localhost:3000/users')
                .then(res => this.items = res.data)
                .then(err => console.log(err))
        },
        //Fetch Data End

        // Update Start
        async updateData(data) {
            await axios.put(`http://localhost:3000/users/${data.id}`, {

                name: data.name,
                email: data.email,
                address: {
                    street: data.address.street,
                    suite: data.address.suite,
                    zipcode: data.address.zipcode,

                },
                phone: data.phone,
                website: data.website,

            })
                .then(res => console.log(res))
                .then(err => console.log(err))
        },
        // Update End

        // Delete Data Start
        async deleteData(data) {

            await axios.delete(`http://localhost:3000/users/${data.id}`)
                .then(this.getData())
                .then(err => console.log(err))
        },
        // Delete Data End

        async addNewRecord() {
            await axios.post('http://localhost:3000/users/', {
                name: this.name,
                email: this.email,
                address: {
                    street: this.street,
                    suite: this.suite,
                    zipcode: this.zipcode,

                },
                phone: this.phone,
                website: this.website,
            }).then(this.getData()).then(err => console.log(err))
        }
        //UPDATE END
    },
    mounted() {
        this.getData();


    }

}
</script>

<style>

</style>
