<template>
    <v-container>
        <v-card>
            <v-container grid-list-md mb-0>
                <h2 class="text-md-center">My Cart</h2>
                <v-data-table :headers="headers" :items="services" v-model="total">
                    <template v-slot:body="{ items }">
                        <tbody>
                            <tr v-for="(item,index) in items" :key="item.id">
                                <td>{{ index + 1 }}</td>
                                <td><v-img max-width="120" :src="require('../../assets/Borneosia.png')"/></td>
                                <td>{{ item.nama}}</td>
                                <td>{{ item.jumlah }}</td>
                                <td>IDR {{ item.harga }}</td>
                                <td >
                                    <v-btn icon color="error" light @click="deleteData(item.id)">
                                        <v-icon>mdi-delete</v-icon>
                                    </v-btn>
                                </td>
                            </tr>
                           <v-btn @click="totals(item.harga)">{{total}}</v-btn>
                        </tbody>
                    </template>
                </v-data-table>
                
            </v-container>
             
        </v-card>
        <v-snackbar v-model="snackbar" :color="color" :multi-line="true" :timeout="3000">
            {{ text }}
            <v-btn dark text @click="snackbar = false">
                Close
            </v-btn>
        </v-snackbar>
    </v-container>
</template>

<script>
    export default {
        data() {
            return {
                dialog: false,
                keyword: '',
                total:  0,
                headers: [{
                        text: 'No',
                        value: 'no',
                    },
                    {
                        text: 'Name',
                        value: 'nama'
                    },
                    {
                        text: 'Image',
                        value: 'harga'
                    },
                    {
                        text: 'Amount',
                        value: 'jumlah'
                    },
                    {
                        text: 'Price',
                        value: 'harga '
                    },
                    {
                        text: 'Remove',
                        value: null
                    },
                ],
                services: [],
                snackbar: false,
                color: null,
                text: '',
                user: new FormData,
                typeInput: 'new',
                errors: '',
                updatedId: '',
            }
        },
        methods: {
            getData() {
                var uri = this.$apiUrl + '/cart'
                this.$http.get(uri).then(response => {
                    this.services = response.data.message
                })
            },
            totals(harga) {
                this.total = 10000;
            },
            sendData() {
                this.user.append('name', this.form.name);
                this.user.append('price', this.form.price);
                this.user.append('type', this.form.type);
                
                var uri = this.$apiUrl + '/user'
                this.load = true
                this.$http.post(uri, this.user).then(response => {
                    this.snackbar = true; //mengaktifkan snackbar
                    this.color = 'green'; //memberi warna snackbar
                    this.text = response.data.message; //memasukkan pesan ke snackbar
                    this.load = false;
                    this.dialog = false;
                    this.getData(); //mengambil data user
                    this.resetForm();
                }).catch(error => {
                    this.errors = error;
                    this.snackbar = true;
                    this.text = 'Try Again';
                    this.color = 'red';
                    this.load = false;
                })
            },
            updateData() {
                this.user.append('name', this.form.name);
                this.user.append('price', this.form.price);
                this.user.append('type', this.form.type);
              
                var uri = this.$apiUrl + '/user/' + this.updatedId;
                this.load = true
                this.$http.post(uri, this.user).then(response => {
                    this.snackbar = true; //mengaktifkan snackbar
                    this.color = 'green'; //memberi warna snackbar
                    this.text = response.data.message; //memasukkan pesan ke snackbar
                    this.load = false;
                    this.dialog = false
                    this.getData(); //mengambil data user
                    this.resetForm();
                    this.typeInput = 'new';
                }).catch(error => {
                    this.errors = error
                    this.snackbar = true;
                    this.text = 'Try Again';
                    this.color = 'red';
                    this.load = false;
                    this.typeInput = 'new';
                })
            },
            editHandler(item) {
                this.typeInput = 'edit';
                this.dialog = true;
                this.form.name = item.name;
                this.form.price = item.price;
                this.form.type = item.type,
              
                this.updatedId = item.id
            },
            deleteData(deleteID) { //mengahapus data
                var uri = this.$apiUrl +
                    '/user/' + deleteID; //data dihapus berdasarkan id
                this.$http.delete(uri).then(response => {
                    this.snackbar = true;
                    this.text = response.data.message;
                    this.color = 'green'
                    this.deleteDialog = false;
                    this.getData();
                }).catch(error => {
                    this.errors = error
                    this.snackbar = true;
                    this.text = 'Try Again';
                    this.color = 'red';
                })
            },
            setForm() {
                if (this.typeInput === 'new') {
                    this.sendData()
                } else {
                    console.log("dddd")
                    this.updateData()
                }
            },
            resetForm() {
                this.form = {
                    name: '',
                    price: '',
                    type: '',
                }
            }
        },
        mounted() {
            if(!localStorage.getItem('token'))
            {
                this.$router.push({ path : "login"})
            }
            this.getData();
        },
    } 
</script>