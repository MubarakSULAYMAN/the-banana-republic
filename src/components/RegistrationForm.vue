<template>
  <form @submit.prevent="save">
    <fieldset class="grid">
      <div class="label-area">
        <span></span>
        <label for="name">Name</label>
      </div>

      <div class="input-area">
        <input
          type="text"
          name="name"
          id="name"
          placeholder="Kendall Jenner"
          v-model="user.fullname"
        />

        <p class="error-message">Section is required</p>
      </div>
    </fieldset>

    <fieldset class="grid">
      <div class="label-area">
        <span></span>
        <legend class="label">Gender</legend>
      </div>

      <div class="input-area">
        <div class="radio-group flex-row">
          <input
            type="radio"
            name="gender"
            id="male"
            value="Male"
            v-model="user.gender"
          />
          <label for="male">Male</label>

          <input
            type="radio"
            name="gender"
            id="female"
            value="Female"
            v-model="user.gender"
          />
          <label for="female">Female</label>
        </div>

        <p class="error-message">Section is required</p>
      </div>
    </fieldset>

    <fieldset class="grid">
      <div class="label-area">
        <span></span>
        <label for="dob">Date of Birth</label>
      </div>

      <div class="input-area">
        <input
          type="text"
          name="dob"
          id="dob"
          placeholder="01/02/1983"
          min="01/07/1952"
          :max="today()"
          onfocus="(this.type='date')"
          onblur="(this.type='text')"
          v-model="user.dob"
        />

        <p class="error-message">Section is required</p>
      </div>
    </fieldset>

    <fieldset :class="[invalid ? 'invalid-input' : '', 'grid']">
      <div class="label-area">
        <span></span>
        <label for="email">Email</label>
      </div>

      <div class="input-area">
        <input
          type="email"
          name="email"
          id="email"
          placeholder="kendall@email.com"
          v-model="user.email"
        />

        <p class="error-message">Section is required</p>
      </div>
    </fieldset>

    <fieldset class="grid">
      <div class="label-area">
        <span></span>
        <label for="mobile">Mobile</label>
      </div>

      <div class="input-area">
        <input
          type="tel"
          name="mobile"
          id="mobile"
          placeholder="+91 98765 43210"
          v-model="user.phone"
        />

        <p class="error-message">Section is required</p>
      </div>
    </fieldset>

    <fieldset class="grid">
      <div class="label-area">
        <span></span>
        <label for="customer-id">Customer ID</label>
      </div>

      <div class="input-area">
        <input
          type="text"
          name="customer-id"
          id="customer-id"
          placeholder="576802-ERD0348 45"
          v-model="user.customerID"
        />

        <p class="error-message">Section is required</p>
      </div>
    </fieldset>

    <fieldset class="grid">
      <div class="label-area">
        <span></span>
        <legend class="label">Membership</legend>
      </div>

      <div class="input-area">
        <div class="radio-group flex-row">
          <!-- <div class="radio-wrap"> -->
          <input
            type="radio"
            name="membership"
            id="classic"
            class="card"
            value="Classic"
            v-model="user.membership"
          />
          <label for="classic">Classic</label>

          <input
            type="radio"
            name="membership"
            id="silver"
            class="card"
            value="Silver"
            v-model="user.membership"
          />
          <label for="silver">Silver</label>

          <input
            type="radio"
            name="membership"
            id="gold"
            class="card"
            value="Gold"
            v-model="user.membership"
          />
          <label for="gold">Gold</label>
        </div>

        <p class="error-message">Section is required</p>
      </div>
    </fieldset>

    <section class="grid">
      <div></div>
      <div class="button-group">
        <button class="cancel" @click="cancel">Cancel</button>
        <button type="submit" class="save">Save</button>
      </div>
    </section>

    <div :class="[saved ? 'saved' : '', 'info']">SAVED SUCCESSFULLY</div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      user: {
        fullname: '',
        gender: '',
        dob: '',
        email: '',
        mobile: '',
        customerID: '',
        membership: '',
      },

      invalid: true,
      saved: false,
    };
  },

  methods: {
    today() {
      const date = new Date();
      let day = date.getDate();
      if (day < 10) {
        day = `0${day}`;
      }

      let month = date.getMonth();
      if (month < 10) {
        month = `0${month}`;
      }

      const year = date.getFullYear();

      return `${day}/${month}/${year}`;
    },

    cancel() {
      this.user = {
        fullname: '',
        gender: '',
        dob: '',
        email: '',
        mobile: '',
        customerID: '',
        membership: '',
        phone: '',
      };
    },

    save() {
      this.saved = true;
      setTimeout(() => {
        this.saved = false;
      }, 2000);

      this.cancel();
    },
  },
};
</script>

<style scoped>
form {
  position: relative;
  width: calc(70% - 20px);
  margin: auto;
  padding: 10px;
}

fieldset,
section {
  grid-template-columns: 1fr 3fr;
  gap: 50px;
}

fieldset {
  border: none;
  padding-bottom: 15px;
}

.label-area {
  padding-top: 15px;
}

span {
  display: inline-block;
  width: 5px;
  height: 5px;
  margin: 0 3px 3px 5px;
  border: 1px solid var(--orange);
  border-radius: 50%;
  background-color: var(--orange);
}

.input-area {
  position: relative;
}

.input-area > input {
  width: 100%;
  padding: 10px;
  border: 2px solid transparent;
  border-radius: 4px;
  background-color: var(--gray-light);
  transition: all 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);
}

.input-area > input::placeholder {
  color: var(--gray);
}

.input-area > input:hover,
.input-area > input:focus {
  color: var(--black);
  border-color: var(--gray);
  outline: transparent;
  background-color: var(--gray-lighter);
  transition-duration: 0.2;
}

.radio-group {
  flex-wrap: wrap;
  width: fit-content;
  width: max-content;
  transform: translate(10px, 10px);
}

[type='radio']:checked,
[type='radio']:not(:checked) {
  position: absolute;
  left: -9999px;
}

[type='radio']:checked + label,
[type='radio']:not(:checked) + label {
  position: relative;
  display: inline-block;
  padding-left: 50px;
  color: var(--gray);
  line-height: 20px;
  cursor: pointer;
}

[type='radio']:checked + label:not(:last-child),
[type='radio']:not(:checked) + label:not(:last-child) {
  padding-right: 20px;
}

[type='radio']:checked + label:before,
[type='radio']:not(:checked) + label:before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  width: 40px;
  height: 40px;
  background-color: var(--gray-light);
  transform: translateY(-10px);
}

#male:checked + label:before,
#male:not(:checked) + label:before {
  background-image: url(../assets/images/icons/mars-symbol.svg);
}

#female:checked + label:before,
#female:not(:checked) + label:before {
  background-image: url(../assets/images/icons/venus-symbol.svg);
}

.card:checked + label:before,
.card:not(:checked) + label:before {
  background-image: url(../assets/images/icons/card.svg);
}

[type='radio']:checked + label:after,
[type='radio']:not(:checked) + label:after {
  content: '';
  position: absolute;
  top: -9px;
  left: 0;
  width: 40px;
  height: 40px;
  background: var(--gray);
  -webkit-transition: all 0.2s ease;
  transition: all 0.2s ease;
}

[type='radio']:not(:checked) + label:after {
  opacity: 0;
  -webkit-transform: scale(0);
  transform: scale(0);
}

[type='radio']:checked + label:after {
  opacity: 1;
  -webkit-transform: scale(1);
  transform: scale(1);
}

#male:checked + label:after,
#male:not(:checked) + label:after {
  background-image: url(../assets/images/icons/mars-symbol--white.svg);
}

#female:checked + label:after,
#female:not(:checked) + label:after {
  background-image: url(../assets/images/icons/venus-symbol--white.svg);
}

.card:checked + label:after,
.card:not(:checked) + label:after {
  background-image: url(../assets/images/icons/card--white.svg);
}

[type='radio']:checked + label:before,
[type='radio']:not(:checked) + label:before,
[type='radio']:checked + label:after,
[type='radio']:not(:checked) + label:after {
  background-position: center;
  background-repeat: no-repeat;
  background-size: 50%;
  border-radius: 100%;
}

.label {
  display: inline-block;
}

.error-message {
  display: none;
  position: absolute;
  bottom: -13px;
  right: 3px;
  color: var(--orange);
  font-size: var(--text-xs);
  text-align: right;
}

.invalid-input {
  color: var(--orange);
  font-weight: 600;
}

.invalid-input span {
  opacity: 1;
}

.invalid-input .input-area > input {
  color: var(--orange);
  border-color: var(--orange);
}

.invalid-input p {
  display: block;
}

.button-group {
  margin: 50px auto 0;
}

button {
  position: relative;
  width: 120px;
  padding: 10px 20px;
  text-transform: uppercase;
  border: 1px solid transparent;
  border-radius: 4px;
}

button:first-child {
  margin-right: 20px;
}

button:hover {
  animation: pop 2s infinite;
  animation-timing-function: ease;
}

button:focus {
  animation: pop 1s;
  animation-timing-function: ease-in-out;
}

button.cancel {
  background-color: var(--gray-light);
}

button.save {
  color: var(--white);
  background-color: var(--teal);
}

.info {
  position: absolute;
  bottom: -60px;
  right: 20px;
  padding: 10px;
  color: var(--teal);
  font-weight: 600;
  border: 2px solid var(--teal);
  border-radius: 5px;
  opacity: 0;
  width: 0;
  height: 0;
}

.saved {
  opacity: 1;
  width: fit-content;
  height: fit-content;
}

@keyframes pop {
  0% {
    transform: scale(1.05, 1.05);
  }

  100% {
    transform: scale(1, 1);
  }
}

@media only screen and (max-width: 768px) {
  form {
    width: calc(90% - 10px);
    padding: 50px 5px;
  }

  fieldset,
  section {
    grid-template-columns: 1.3fr 3fr;
  }

  button {
    width: 110px;
  }

  button:first-child {
    margin-right: 10px;
  }

  .info {
    position: absolute;
    bottom: -20px;
    transform: translateX(5%);
  }
}

@media only screen and (max-width: 425px) {
  form {
    width: 100%;
    margin-top: 0;
    padding: 30px 10px;
  }

  fieldset {
    padding-bottom: 20px;
  }

  fieldset,
  section {
    grid-template-columns: 1fr;
    gap: 0;
  }

  .label-area {
    padding-top: 0;
    margin-bottom: 0;
  }

  .button-group {
    margin: 0;
    margin-top: 20px;
  }

  button {
    width: 100%;
  }

  button:first-child {
    margin-right: 0;
    margin-bottom: 10px;
  }

  .info {
    position: absolute;
    bottom: 5px;
    right: 50%;
    transform: translateX(50%);
  }
}
</style>
