<template>
  <div>
    <form @submit.prevent="submitForm">
      <h3>Enter for your chance to win!</h3>
      <div class="table-container">
        <table class="responsive-table">
          <tr>
            <td>
              <label for="firstName" class="important">First Name </label>
            </td>
            <td>
              <input
                type="text"
                id="firstName"
                v-model.trim="firstName.val"
                @blur="clearValidity('firstName')"
                :class="{ invalid: !firstName.isValid }"
              />
            </td>
          </tr>
          <tr>
            <td>
              <label for="lastName" class="important">Last Name </label>
            </td>
            <td>
              <input
                type="text"
                id="lastName"
                v-model.trim="lastName.val"
                @blur="clearValidity('lastName')"
                :class="{ invalid: !lastName.isValid }"
              />
            </td>
          </tr>
          <tr>
            <td><label for="email" class="important"> Email </label></td>
            <td>
              <input
                type="email"
                id="email"
                v-model.trim="email.val"
                @blur="clearValidity('email')"
                :class="{ invalid: !email.isValid }"
              />
            </td>
          </tr>
          <tr>
            <td>
              <label for="confirmEmail" class="important">Confirm Email </label>
            </td>
            <td>
              <input
                type="email"
                id="confirmEmail"
                v-model.trim="confirmEmail.val"
                @blur="clearValidity('confirmEmail')"
                :class="{ invalid: !confirmEmail.isValid }"
              />
            </td>
          </tr>
          <tr>
            <td>
              <label for="address1" class="important">Address 1 </label>
            </td>
            <td>
              <input
                type="text"
                id="address1"
                v-model.trim="address1.val"
                @blur="clearValidity('address1')"
                :class="{ invalid: !address1.isValid }"
              />
            </td>
          </tr>
          <tr>
            <td>
              <label for="address2" class="important">Address 2 </label>
            </td>
            <td>
              <input
                type="text"
                id="address2"
                v-model.trim="address2.val"
                @blur="clearValidity('address2')"
                :class="{ invalid: !address2.isValid }"
              />
            </td>
          </tr>
          <tr>
            <td><label for="city" class="important"> City </label></td>
            <td>
              <input
                type="text"
                id="city"
                v-model.trim="city.val"
                @blur="clearValidity('city')"
                :class="{ invalid: !city.isValid }"
              />
            </td>
          </tr>
          <tr>
            <td>
              <label for="state" class="important"> State/Province </label>
            </td>
            <td>
              <select
                v-model="selectedState.val"
                @blur="clearValidity('selectedState')"
                :class="{ invalid: !selectedState.isValid }"
              >
                <option value="">Select a state</option>
                <option v-for="state in states" :key="state" :value="state">
                  {{ state }}
                </option>
              </select>
            </td>
          </tr>
          <tr>
            <td>
              <label for="zip" class="important"> Zip/Postal Code </label>
            </td>
            <td>
              <input
                type="number"
                id="zip"
                v-model.trim="zip.val"
                @blur="clearValidity('zip')"
                :class="{ invalid: !zip.isValid }"
              />
            </td>
          </tr>
          <tr>
            <td><label for="phone" class="important"> Phone No. </label></td>
            <td>
              <input
                type="number"
                id="phone"
                v-model.trim="phone.val"
                @blur="clearValidity('phone')"
                :class="{ invalid: !phone.isValid }"
              />
            </td>
          </tr>
          <tr>
            <td></td>
            <td>
              <input
                type="checkbox"
                name="confirm"
                id="confirm"
                v-model="confirm.val"
                @blur="clearValidity('confirm')"
                :class="{ invalid: !confirm.isValid }"
              />
              <span
                ><span class="important-color">*</span> I have read and agree to
                the
                <br />
                <a href="#"> Official Rules</a> and
                <a href="#">Privacy Policy</a></span
              >
            </td>
          </tr>
        </table>
      </div>
      <p v-if="!formIsValid">
        <span class="important-color">*</span>required fields
      </p>
      <div>
        <button>Submit</button>
      </div>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      firstName: {
        val: "",
        isValid: true,
      },
      lastName: {
        val: "",
        isValid: true,
      },
      email: {
        val: "",
        isValid: true,
      },
      confirmEmail: {
        val: "",
        isValid: true,
      },
      confirm: {
        val: false,
        isValid: true,
      },
      address1: {
        val: "",
        isValid: true,
      },
      address2: {
        val: "",
        isValid: true,
      },
      city: {
        val: "",
        isValid: true,
      },
      selectedState: {
        val: "",
        isValid: true,
      },
      states: [
        "Andhra Pradesh",
        "Arunachal Pradesh",
        "Assam",
        "Bihar",
        "Chhattisgarh",
        "Goa",
        "Gujarat",
        "Haryana",
        "Himachal Pradesh",
        "Jharkhand",
        "Karnataka",
        "Kerala",
        "Madhya Pradesh",
        "Maharashtra",
        "Manipur",
        "Meghalaya",
        "Mizoram",
        "Nagaland",
        "Odisha",
        "Punjab",
        "Rajasthan",
        "Sikkim",
        "Tamil Nadu",
        "Telangana",
        "Tripura",
        "Uttar Pradesh",
        "Uttarakhand",
        "West Bengal",
        "Andaman and Nicobar",
        "Chandigarh",
        "Daman and Diu",
        "Delhi",
        "Lakshadweep",
        "Puducherry",
      ],
      zip: {
        val: "",
        isValid: true,
      },
      phone: {
        val: "",
        isValid: true,
      },
      formIsValid: true,
    };
  },
  methods: {
    clearValidity(input) {
      this[input].isValid = true;
    },
    submitForm() {
      this.formValidate();
      if (!this.formIsValid) {
        return;
      }
      alert("Submitted succesfully");
      this.firstName.val = "";
      this.lastName.val = "";
      this.email.val = "";
      this.confirmEmail.val = "";
      this.confirm.val = false;
      this.phone.val = "";
      this.address1.val = "";
      this.address2.val = "";
      this.selectedState.val = "";
      this.city.val = "";
      this.zip.val = "";
    },
    formValidate() {
      this.formIsValid = true;
      if (this.firstName.val == "") {
        this.firstName.isValid = false;
        this.formIsValid = false;
      }
      if (this.lastName.val == "") {
        this.lastName.isValid = false;
        this.formIsValid = false;
      }
      if (this.email.val == "") {
        this.email.isValid = false;
        this.formIsValid = false;
      }
      if (this.confirmEmail.val == "") {
        this.confirmEmail.isValid = false;
        this.formIsValid = false;
      }
      if (this.email.val !== this.confirmEmail.val) {
        this.confirmEmail.isValid = false;
        this.formIsValid = false;
      }
      if (this.address1.val == "") {
        this.address1.isValid = false;
        this.formIsValid = false;
      }
      if (this.address2.val == "") {
        this.address2.isValid = false;
        this.formIsValid = false;
      }
      if (this.city.val == "") {
        this.city.isValid = false;
        this.formIsValid = false;
      }
      if (this.selectedState.val == "") {
        this.selectedState.isValid = false;
        this.formIsValid = false;
      }
      if (this.zip.val == "") {
        this.zip.isValid = false;
        this.formIsValid = false;
      }
      if (this.phone.val == "") {
        this.phone.isValid = false;
        this.formIsValid = false;
      }
      if (this.confirm.val == false) {
        this.confirm.isValid = false;
        this.formIsValid = false;
      }
    },
  },
};
</script>
<style scoped>
table td {
  text-align: right;
}

th,
td {
  padding: 10px;
}

form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.invalid {
  border-color: red;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  /* width: 100%; */
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: 200px;
}

input[type="checkbox"],
input[type="radio"] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type="checkbox"] + label,
input[type="radio"] + label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #e92208;
  background-color: #e92208;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 5px;
  margin: 10px 25px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}

.important::after {
  content: " *";
  color: red;
}
.important-color {
  color: red;
}
input[type="checkbox"][data-v-2b2b3f56] {
  display: inline-block;
  width: auto;
  margin-right: 0.5rem;
}
.table-container {
  overflow-x: auto;
}

.responsive-table {
  width: 100%;
  border-collapse: collapse;
}

.responsive-table th,
.responsive-table td {
  padding: 8px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}
.select-container {
  width: 100%;
}

.responsive-select {
  padding: 4px 0;
}

@media (max-width: 480px) {
  .responsive-table {
    display: block;
    overflow-x: auto;
    white-space: nowrap;
  }

  input,
  select {
    margin-top: 0;
  }

  .responsive-table thead,
  .responsive-table tbody,
  .responsive-table th,
  .responsive-table td,
  .responsive-table tr {
    display: block;
  }

  .responsive-table thead tr {
    position: absolute;
    top: -9999px;
    left: -9999px;
  }

  .responsive-table tbody tr {
    border-bottom: 1px solid #ddd;
  }

  .responsive-table td {
    border-bottom: none;
    position: relative;
  }

  .responsive-table td:before {
    position: absolute;
    top: 6px;
    left: 6px;
    width: 45%;
    padding-right: 10px;
    white-space: nowrap;
    content: attr(data-label);
    font-weight: bold;
  }
}
</style>
