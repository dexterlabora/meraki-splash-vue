<template>
<div>
  <!-- Card -->
  <div class="col-sm-10 offset-sm-1 offset-md-4 col-md-4 text-center">
    <div class="card mx-md-4">

        <!-- Card body -->
        <div class="card-body">

            <!-- Default form subscription -->
            <form @submit.prevent="onSubmit">
                <p class="h4 text-center py-4">WiFi Access</p>

                <label for="lastName" class="grey-text font-weight-light">Last Name</label>
                <input type="text" id="lastName" class="form-control">
                
                <br>

                <label for="roomNumber" class="grey-text font-weight-light">Room Number</label>
                <input type="text" id="defaultFormCardEmailEx" class="form-control">
                <br>
                <label for="terms" ><a href="/terms">Agree to T&S</a></label>
                <input type="checkbox" required=true id="terms" v-model="form.terms">

                <div class="text-center py-4 mt-3">
                    <button class="btn btn-outline-primary" type="submit">Login<i class="fa fa-paper-plane-o ml-2"></i></button>
                </div>
            </form>
            <!-- Default form subscription -->

        </div>
        <!-- Card body -->

    </div>
  <!-- Card -->
  </div> 


  <p><label>Client MAC: </label>{{ clientMac }}</p>

</div>
 
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      clientMac: '',
      baseGrantUrl: '',
      userContinueUrl: '',
      clientIp:'',
      nodeMac: '',
      form: {
        lastName: '',
        room: '',
        email: '',
        terms: false
      }
    }
  },
  computed: {
    loginUrl(){
      return this.baseGrantUrl+"?continue_url="+this.userContinueUrl
    }
  },
  created() {
  console.log('route query', this.$route.query);
  this.clientMac = this.$route.query.client_mac;
  this.baseGrantUrl = this.$route.query.base_grant_url;
  this.userContinueUrl = this.$route.query.user_continue_url
  this.clientIp = this.$route.query.client_ip
  this.nodeMac = this.$route.query.node_mac
  },
  methods: {
    onSubmit(){
      // verify data

      // authorize client (search DB)

      // login to meraki
      this.merakiLogin();
    },
    merakiLogin(){
        console.log("Form data submitted");

        if (!this.baseGrantUrl){
          console.log("login failed, no base grant url");
          return;
        }
        // ** Login to Meraki by redirecting client to the base_grant_url **
        console.log("Redirecting to base_grant_url: ",this.loginUrl);
        window.location.href = this.loginUrl;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}


</style>
