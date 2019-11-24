<template>
    <div class="ma-5 pa-5">
        <v-container class="grey lighten-5">
            <v-card class="pa-2" outlined tile>
            <v-row>
                <v-col md="4">
                    <v-card class="grey lighten-2">
                        <v-img src="../../assets/Nicho.jpg" width="400" height="400">
                        </v-img>
                    </v-card>
                </v-col>
                <v-col>
                    <v-row class="pb-10">
                        <v-col>
                            Name :
                            
                        </v-col>
                    </v-row>
                    <v-row class="pb-10">
                        <v-col>
                            Email :

                        </v-col>
                    </v-row>
                    <v-row class="pb-10">
                        <v-col>
                            Phone Number :

                        </v-col>
                    </v-row>
                    <v-row class="pb-10">
                        <v-col>
                            Address :
                            
                        </v-col>
                    </v-row>
                </v-col>
            </v-row>
            <v-card-actions>
                <v-spacer></v-spacer>
                <v-row align="center">
                    <div class="my-2">
                        <v-btn color="success" dark large href="editprofile">Edit Profile</v-btn>
                    </div>
                </v-row>
            </v-card-actions>
            </v-card>
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
