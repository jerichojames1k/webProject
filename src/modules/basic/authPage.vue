<template>
  <div id="authPage">
    <b-container fluid>
      <b-row>
        <b-col cols="1"></b-col>
        <b-col>
          <div id="form">
            <b-card id="card">
              <b-card-text class="center">
                <b>AUTHORIZATION LETTER</b>
              </b-card-text>
              <br />
              <b-card-text id="senderName" class="center">
                <p>{{UpdateSenderName}}</p>
              </b-card-text>
              <b-card-text class="center">
                <p>{{UpdateyourAddress}}</p>
              </b-card-text>
              <b-card-text class="center">
                <p>{{Updatezip}}</p>
              </b-card-text>
              <br />
              <br />

              <b-card-text>
                <p>{{UpdatecurrentDate}}</p>
              </b-card-text>
              <br />

              <b-card-text>
                <p>{{UpdaterecName}}</p>
              </b-card-text>
              <b-card-text>{{UpdaterecAddress}}</b-card-text>
              <b-card-text class="side">
                <p>{{UpdaterecZip}}</p>
              </b-card-text>
              <b-card-text class="side">
                <p>{{Updatesubject}}</p>
              </b-card-text>
              <br />

              <b-card-text class="side">
                <b>To whom it may concern:</b>
              </b-card-text>
              <b-card-text class="side">
                <!-- NEEED FOOOORRR CHANNNNNNNNGE -->
               <p> I __________{{UpdateOwnerofdocs}}hereby authorize ________________ {{Updateauthorizeperson}}permission to process and
                collect my ________________{{UpdateauthDocument}}in my behalf. To expedite the process, I've included Identification
                information for verification needs.</p>
              </b-card-text>
              <b-card-text><p>Authorized Person: [Recipient's name]{{UpdateRecipientName}}</p></b-card-text>
              <b-card-text><p>Identity Type: [Type of ID]{{UpdateTypeofId}}</p></b-card-text>
              <b-card-text><p>ID Number:[ID number]{{UpdateIdNumber}}</p></b-card-text>
              <b-card-text>
                <p>Scoped of Authorization:{{Updatedoc}}</p>
              </b-card-text>
              <b-card-text><p>The Permission to processes the documents in my name starts on ________________ {{UpdateStardate}}and ends on ________________{{UpdateEndates}}</p></b-card-text>
              <br />

              <b-card-text class="side">Sincerely,</b-card-text>
              <b-card-text class="side">
                <p>{{UpdateSenderName}}</p>
              </b-card-text>
              <b-card-text class="side">
                <p>{{UpdatedueDate}}</p>
              </b-card-text>
            </b-card>
          </div>
          <br />
          <br />
          <div>
            <b-button v-b-modal.modalForm id="fillUp" @click="show=true">Fill Up</b-button>
            <b-button v-b-modal.sendToModal id="sendTo" @click="shows=true">Send To</b-button>
          </div>
        </b-col>
        <b-col cols="1"></b-col>
      </b-row>
    </b-container>

    <b-modal
      size="lg"
      scrollable
      id="modalForm"
      ref="modal"
      title="Please Fill Up Everything"
      @show="resetModal"
      @hidden="resetModal"
      @ok="handleOk"
      no-close-on-esc
      no-close-on-backdrop
      hide-header-close
      ok-variant="success"
      cancel-variant="primary"
      v-model="show"
    >
      <form ref="form" @submit.stop.prevent="handleSubmit">
        <!-- Sender's Credentials -->
        <b-form-group
          :state="nameState"
          label="Sender's Full Name"
          label-for="yourName"
          invalid-feedback="Sender's Full Name is required"
        >
          <b-form-input
            class="borderColor"
            id="yourName"
            v-model="SenderName"
            :state="nameState"
            required
            placeholder="Sender's Full Name"
          ></b-form-input>
        </b-form-group>
        <b-form-group
          :state="nameState"
          label="Sender's Address"
          label-for="yourAddress"
          invalid-feedback="Address is required"
        >
          <b-form-input
            class="borderColor"
            id="yourAddress"
            v-model="yourAddress"
            :state="nameState"
            required
            placeholder="Sender's Current Address"
          ></b-form-input>
        </b-form-group>
        <b-form-group
          :state="nameState"
          label="Sender's State/ZIP Code"
          label-for="zip"
          invalid-feedback="State/Zip Code is required"
        >
          <b-form-input
            class="borderColor"
            id="zip"
            v-model="zip"
            :state="nameState"
            required
            placeholder="State/ZIP Code"
          ></b-form-input>
        </b-form-group>
        <!-- Date from & Date to -->
        <b-form-group
          :state="nameState"
          label="Current Date"
          label-for="currentDate"
          invalid-feedback="Date is required"
        >
          <b-form-input
            class="borderColor"
            id="currentDate"
            v-model="currentDate"
            :state="nameState"
            required
            placeholder="Current Date"
          ></b-form-input>
        </b-form-group>
        <b-form-group
          :state="nameState"
          label="Due Date"
          label-for="dueDate"
          invalid-feedback="Date is required"
        >
          <b-form-input
            class="borderColor"
            id="dueDate"
            v-model="dueDate"
            :state="nameState"
            required
            placeholder="Due Date"
          ></b-form-input>
        </b-form-group>
        <!-- Recipient's Credentials -->
        <b-form-group
          :state="nameState"
          label="Recipient's Full Name"
          label-for="recName"
          invalid-feedback="Recipient's Full Name is required"
        >
          <b-form-input
            class="borderColor"
            id="recName"
            v-model="recName"
            :state="nameState"
            required
            placeholder="Recipient's Full Name"
          ></b-form-input>
        </b-form-group>
        <b-form-group
          :state="nameState"
          label="Recipient's Address"
          label-for="recAddress"
          invalid-feedback="Recipient's Address is required"
        >
          <b-form-input
            class="borderColor"
            id="recAddress"
            v-model="recAddress"
            :state="nameState"
            required
            placeholder="Recipient's Address"
          ></b-form-input>
        </b-form-group>
        <b-form-group
          :state="nameState"
          label="Recipient's State/ZIP Code"
          label-for="recZip"
          invalid-feedback="Recipient's State/Zip Code is required"
        >
          <b-form-input
            class="borderColor"
            id="recZip"
            v-model="recZip"
            :state="nameState"
            required
            placeholder="Recipient's State/Zip Code"
          ></b-form-input>
        </b-form-group>
        <!-- Subject -->
        <b-form-group
          :state="nameState"
          label="Subject"
          label-for="subject"
          invalid-feedback="Subject is required"
        >
          <b-form-input
            class="borderColor"
            id="subject"
            v-model="subject"
            :state="nameState"
            required
            placeholder="Subject"
          ></b-form-input>
        </b-form-group>
        <!-- Types of Documents -->
        <b-form-group
          :state="nameState"
          label="Types of Document/s"
          label-for="doc"
          invalid-feedback="Type of Document is required"
        >
          <b-form-input
            class="borderColor"
            id="doc"
            v-model="doc"
            :state="nameState"
            required
            placeholder="e.g Birth Certificate"
          ></b-form-input>
        </b-form-group>
      </form>
    </b-modal>

    <!-- Send To -->
    <div>
      <b-modal id="sendToModal" centered title="Recepient's Email">
        <form>
          <b-form-group label="Email" label-for="email" invalid-feedback="Email is required">
            <b-form-input
              class="borderColor"
              id="email"
              :state="nameState"
              required
              placeholder="you@gmail.com"
            ></b-form-input>
          </b-form-group>
        </form>
      </b-modal>
    </div>
  </div>
</template>


<script>
import ROUTER from "router";
export default {
  name: "authForm",
  data() {
    return {
      show: false,
      shows: false,
      UpdateSenderName: "[SenderName]",
      UpdateyourAddress: "[Address]",
      Updatezip: "[State/ ZIP Code]",
      UpdatecurrentDate: "[Date]",
      UpdatedueDate: "[DueDate]",
      UpdaterecName: "[Recipients name]",
      UpdaterecAddress: "[Address]",
      UpdaterecZip: "[State/ ZIP Code]",
      Updatesubject: "[Subject]",
      Updatedoc: "[DOCS]",
      nameState: null,
      submittedNames: [],
      modalShow: false
    };
  },
  component: {},
  methods: {
    checkFormValidity() {
      const valid = this.$refs.form.checkValidity();
      this.nameState = valid ? "valid" : "invalid";
      return valid;
    },
    resetModal() {
      this.yourName = "";
      this.nameState = null;
    },
    handleOk(bvModalEvt) {
      // Prevent modal from closing
      bvModalEvt.preventDefault();
      // Trigger submit handler
      this.handleSubmit();
      //replace data
    },
    handleSubmit() {
      // Exit when the form isn't valid
      if (!this.checkFormValidity()) {
        return;
      }
      else{
      console.log(
        "{The modal is successfully tested!!!!!!!!authorization letter!!!!}"
      );
        this.UpdateSenderName = this.SenderName;
        this.UpdateyourAddress = this.yourAddress;
        this.Updatezip = this.zip;
        this.UpdatecurrentDate = this.currentDate;
        this.UpdatedueDate = this.dueDate;
        this.UpdaterecName = this.recName;
        this.UpdaterecAddress = this.recAddress;
        this.UpdaterecZip = this.recZip;
        this.Updatesubject = this.subject;
        this.Updatedoc = this.doc;
        //BLANK THE AREA OR FIELD
        // this.SenderName =" ";
        // this.yourAddress =" ";
        // this.zip =" ";
        // this.currentDate =" ";
        // this.dueDate =" ";
        // this.recName =" ";
        // this.recAddress =" ";
        // this.recZip =" ";
        // this.subject =" ";
        // this.doc =" ";
      }
      // Push the name to submitted names
      //this.submittedNames.push(this.yourName);
      // Hide the modal manually
      this.$nextTick(() => {
        this.$refs.modal.hide();
      });
    }
  }
};
</script>
<style lang='scss' scoped>
@import "~assets/color.scss";
#authPage {
  margin-top: 6%;
}
#sendTo {
  background-color: $motif;
  margin-bottom: 3%;
  width: 20%;
  float: right;
}
#fillUp {
  background-color: $motif;
  margin-bottom: 3%;
  width: 20%;
  float: left;
}
.center {
  text-align: center;
}
#card,
.borderColor {
  border-color: $motif;
}
</style>
