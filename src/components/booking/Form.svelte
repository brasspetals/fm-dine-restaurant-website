<script>
import {fade} from 'svelte/transition'
import NumPeople from './NumPeople.svelte'

let values = {
    name: '',
    email: '',
    month: '',
    day: '',
    year: '',
    hour: '',
    minute: '',
    selected: 'AM'
  }

let errors = {
  name: false,
  email: false,
  date: false,
  time: false
}

let errorMsgs = {
  name: '',
  email: '',
  date: '',
  time: ''
}
 
// NAME VALIDATION
 const validateName = () => {
  if (values.name == "" || values.name == undefined) {
    errorMsgs.name = "This field is required."
    errors.name = true
  } else {
    errorMsgs.name = ""
    errors.name = false
  }
}
 
// EMAIL VALIDATION
const validateEmail = () => {
  const emailRegex = /^[a-zA-Z][a-zA-Z0-9\-\_\.]+@[a-zA-Z0-9]{2,}\.[a-zA-Z0-9]{2,}$/
  errors.email = true
  
  if (values.email == "" || values.email == undefined) {
    errorMsgs.email = "This field is required."
  } else if (!values.email.match(emailRegex)) {
    errorMsgs.email = "Please use a valid email address."
  } else {
    errorMsgs.email = ""
    errors.email = false
  }
}

// DATE VALIDATION
const validateDate = () => { 
  const reservationDate = new Date(values.year, (values.month - 1), values.day)
  console.log(reservationDate)
  const currentDate = new Date()
  
  if (values.month === '' || values.day === '' || values.year === '' ) {
    errors.date = true
    errorMsgs.date = "This field is incomplete."
  } 
  else if (reservationDate.getTime() < currentDate.getTime()) {
    errors.date = true
    errorMsgs.date = "The date must be today or later."
  } else {
    errors.date = false
    errorMsgs.date = ''
  }
}

// TIME VALIDATION
const validateTime = () => {
  const dayOfWeek = new Date(values.year, (values.month - 1), values.day).toLocaleString('default', {weekday: 'short'})
  console.log(dayOfWeek)
  
  if (values.hour === '' || values.minute === '' ) {
    errors.time = true
    errorMsgs.time = "This field is incomplete."
  } else if (values.selected == 'AM' && values.hour < 9) { 
    errors.time = true
    errorMsgs.time = "Invalid time. Please check open hours."
  } else if (
    (values.selected == 'PM' && (dayOfWeek == 'Sat' || dayOfWeek == 'Sun')) 
    && values.hour >= 11 && values.minute > 29) {
    errors.time = true
    errorMsgs.time = "Invalid time. Please check open hours."
  } else if (
    (values.selected == 'PM' && (dayOfWeek !== 'Sat' || dayOfWeek !== 'Sun')) 
    && values.hour >= 10) {
    errors.time = true
    errorMsgs.time = "Invalid time. Please check open hours."
  } else {
    errors.time = false
    errorMsgs.time = ''
  }
}

// FORM VALIDATION
const validateForm = () => {
  validateName();
  validateEmail();
  validateDate();
  validateTime();
}
</script>


  <form action="#" class="form shadow" on:submit|preventDefault="{validateForm}">
    <div class="input-container">
      <input class:invalid={errors.name} type="text" name="name" id="name" placeholder="Name"
      aria-label="Name" aria-invalid="false" aria-describedby="error-name" bind:value={values.name}>
      {#if errors.name}
        <p id="error-name" class="error error--input" transition:fade>{errorMsgs.name}</p>
      {/if}
    </div>
    <div class="input-container">
      <input class:invalid={errors.email} type="email" name="email" id="email" placeholder="Email"
      aria-label="Email address" aria-invalid="false" aria-describedby="error-email" bind:value={values.email}>
      {#if errors.email}
        <p id="error-email" class="error error--input" transition:fade>{errorMsgs.email}</p>
      {/if}
    </div>
    <fieldset>
      <div class="legend-container">
        <legend class:invalid={errors.date}>Pick a date</legend>
        {#if errors.date}
          <p id="error-date" class="error error--pick" transition:fade>{errorMsgs.date}</p>
        {/if}
      </div>
      <div class="pick-container" id="date">
        <input class:invalid={errors.date} type="number" name="month" id="month" min="01" max="12" placeholder="MM" bind:value={values.month}>
        <input class:invalid={errors.date} type="number" name="day" id="day" min="01" max="31" placeholder="DD" bind:value={values.day}>
        <input class:invalid={errors.date} type="number" name="year" id="year" min="2022" max="2025" placeholder="YYYY" bind:value={values.year}>
      </div>
    </fieldset>
    <fieldset>
      <div class="legend-container">
        <legend class:invalid={errors.time}>Pick a time</legend>
        {#if errors.time}
         <p id="error-time" class="error error--pick">{errorMsgs.time}</p>
        {/if}
      </div>
      <div class="pick-container">
        <input class:invalid={errors.time} type="number" name="hour" id="hour" min="01" max="12" placeholder="09" bind:value={values.hour}>
        <input class:invalid={errors.time} type="number" name="minute" id="minute" min="00" max="59" placeholder="00" bind:value={values.minute}>
        <select bind:value={values.selected} class:invalid={errors.time}>
          <option value="AM">AM</option>
          <option value="PM">PM</option>
        </select>
      </div>
    </fieldset>
    <NumPeople/>
    <button class="submit" type="submit" >Make Reservation</button>
  </form>

<style>
  .invalid,
  .invalid::placeholder {
    color: var(--color-red);
    border-color: var(--color-red);
  }

  .invalid:active {
    color: var(--soft-black);
  }

  .form {
    display: grid;
    gap: 2rem;
    padding: 2rem;
    background-color: var(--color-white);
    max-width: 33.75rem;
    margin: 0 auto;
  }

  .input-container,
  .legend-container {
    position: relative;
  }

  .error--input {
    bottom: -1.5rem;
    left: 1rem;
  }

  .error--pick {
    top: 5.5625rem;
  }

  input, 
  select {
    border-bottom: 0.0625rem solid #8E8E8E;
    color: var(--color-soft-black);
    font-size: 1.125rem;
    line-height: 1.556;
    letter-spacing: -0.0138rem;
    padding: 0 1rem 1rem;
    width: 100%;
    caret-color: var(--color-brown);
    transition: border .5s ease;
    position: relative;
  }

  select {
    -webkit-appearance: none;
    -moz-appearance: none;
    -ms-appearance: none;
    appearance: none;
    background-image: url('/images/icons/icon-arrow.svg');
    background-repeat: no-repeat;
    background-position-x: 3.375rem;
    background-position-y: 0.5rem;
    padding: 0 0 1rem 12px;
  }

  option {
    background-color: var(--color-white);
    color: var(--color-soft-black);
    border: none;
    padding: 2rem;
  }

  input::placeholder {
    color: var(--color-soft-black);
    opacity: 0.5;
  }

  input:focus-within {
    border-bottom: 0.0625rem solid var(--color-soft-black);
  }

  legend {
    font-size: 1.125rem;
    line-height: 1.556;
    letter-spacing: -0.0138rem;
    padding-bottom: 0.5rem;
  }

  fieldset {
    border: none;
    position:relative;
  }

  .pick-container {
    display: grid;
    grid-auto-flow: column;
    grid-template-columns: repeat(2, minmax(min-content, 4.5625rem)) minmax(min-content, 5.5rem);
    gap: 0.9375rem;
    justify-content: start;
  }

  input[type="number"] {
    text-transform: uppercase;
    padding: 0 0 1rem 0.875rem;
    -moz-appearance: textfield;
  }

  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  .submit {
    display: grid;
    justify-content: center;
    align-items: center;
    height: 4rem;
    background-color: var(--color-soft-black);
    border: 0.0625rem solid var(--color-soft-black);
    color: var(--color-white);
    font-size: 0.875rem;
    font-weight: 600;
    line-height: 1.143;
    letter-spacing: 0.125rem;
    text-transform: uppercase;
    transition: background-color .5s ease, color .5s ease;
  }

  .submit:hover {
    color: var(--color-soft-black);
    background-color: var(--color-white);
    transition: background-color .5s ease, color .5s ease;
  }

  @media screen and (min-width: 31.25rem) {
    fieldset {
      display: grid;
      grid-auto-flow: column;
      justify-content: start;
      align-items: center;
      gap: 2rem;
    }

    .error--pick {
      top: 1.6875rem;
    }


    legend {
      min-width: 7.5rem;
      padding-bottom: 0;
    }
  }

  @media screen and (min-width: 37.5rem) {
    .form {
      padding: 3rem;
    }

    fieldset {
      gap: 2.25rem;
    }

    .pick-container {
      grid-template-columns: repeat(2, minmax(min-content, 5rem)) 1fr;
    }

    select {
      width: 6.0625rem;
      background-position-x: 4rem;
    }
  }
</style>