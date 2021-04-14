<template>
<div>
  <div v-if="stepOne">
    <form @submit.prevent="submitPasswordOne()">
      <div class="col-sm-12">
        <div class="col-sm-12">
          <div class="form-group">
            <b>Welcome to Eternal Blue</b><br />
            The riddle is to find the correct password
            <input
              type="password"
              class="form-control"
              v-model="passwordOne"
              id="passwordOne"
              placeholder="Password"
            />
            <input
              type="hidden"
              value="98 108 117 101 98 49 117 101 66 108 117 101"
            />
          </div>
          <button type="submit" class="btn btn-primary">Submit</button>
        </div>
      </div>
    </form>
  </div>
  <div v-if="stepTwo">
      <form @submit.prevent="submitPasswordTwo()">
      <div class="col-sm-12">
        <div class="col-sm-12">
          <div class="form-group">
            <b>Two step authentication</b><br />
            Let's try another one, the answer is inside:
            <p><img src="../assets/BlueHint.jpg"></p>
            Please insert the second password:
            <input
              type="password"
              class="form-control"
              v-model="passwordTwo"
              id="passwordTwo"
              placeholder="Password"
            />
            <input
              type="hidden"
              value="98 108 117 101 98 49 117 101 66 108 117 101"
            />
          </div>
          <button type="submit" class="btn btn-primary">Submit</button>
        </div>
      </div>
    </form>
  </div>
  <div v-if="stepThree">
      <form @submit.prevent="downloadTask()">
      <b>Congratulations</b><br />
      Wow well done, you broke the EternalBlue website. But you made it through the pre-qualification!<br />
      Now just a small code challange and we are done :)
      <p><button class="btn btn-success" type="submit">Download</button></p>
      </form>
  </div>
</div>
</template>

<script>
export default {
  name: "home",

  data() {
    return {
      passwordOne: "",
      passwordTwo: "",
      decryptPasswordOne: "blueb1ueBlue",
      decryptPasswordTwo: "blue1sF0rev3r",

      stepOne: true,
      stepTwo: false,
      stepThree: false
    };
  },

  methods: {
    submitPasswordOne: function() {
      if (this.passwordOne == this.decryptPasswordOne) {
        this.stepOne = false;
        this.stepTwo = true;
      } else {
        alert("Incorrect password");
      }
    },

    submitPasswordTwo: function() {
      if (this.passwordTwo == this.decryptPasswordTwo) {
        this.stepOne = false;
        this.stepTwo = false;
        this.stepThree = true;
      } else {
        alert("Incorrect password");
      }
    },

    downloadTask: function() {
      window.open('TASK.md');
    }
  }
};
</script>
