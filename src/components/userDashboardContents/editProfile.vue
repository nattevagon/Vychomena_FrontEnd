<template>
    <div class="ma-5 pa-5">
        <v-container class="grey lighten-5">
            <v-row>
                <v-col md="4">
                    <v-card class="pa-2" outlined tile>
                        <v-img src="../../assets/Nicho.jpg" width="400" height="400">
                        </v-img>
                    </v-card>
                </v-col>
                <v-col>
                    <v-row>
                        <v-col>
                            Name :
                            <v-text-field>

                            </v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col>
                            Email :
                            <v-text-field>

                            </v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col>
                            Phone Number :
                            <v-text-field>

                            </v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col>
                            Address :
                            <v-text-field>

                            </v-text-field>
                        </v-col>
                    </v-row>
                </v-col>
            </v-row>
            <v-card-actions>
                <v-spacer></v-spacer>
                <v-row align="center">
                    <div class="my-2">
                        <v-btn color="success" dark large>Update Profile</v-btn>
                    </div>
                </v-row>
            </v-card-actions>
        </v-container>
    </div>
</template>
<script>
export default {
    data(){
        return {
        }
    },
    mounted(){
        if(!localStorage.getItem('token'))
        {
            this.$router.push({ path : "login"})
        }
    }
}
</script>
