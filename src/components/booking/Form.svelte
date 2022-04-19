<script>
 import NumPeople from './NumPeople.svelte'
 
 let errorName = false
 let errorNameMsg = "This field is required"
 let errorEmail = false
 let errorEmailMsg = "This field is required"
 let errorDate = false
 let errorDateMsg = "This field is incomplete"
 let errorTime = false
 let errorTimeMsg = "This field is incomplete"

</script>


<div class="pattern-wrap">
  <form action="#" class="form">
    <div class="input-container">
      <input class:invalid={errorName} type="text" name="name" id="name" placeholder="Name"
      aria-label="Name" aria-invalid="false" aria-describedby="error-name" required>
      {#if errorName}
        <p id="error-name" class="error error--input">{errorNameMsg}</p>
      {/if}
    </div>
    <div class="input-container">
      <input class:invalid={errorEmail} type="email" name="email" id="email" placeholder="Email"
      aria-label="Email address" aria-invalid="false" aria-describedby="error-email" required>
      {#if errorEmail}
        <p id="error-email" class="error error--input">{errorEmailMsg}</p>
      {/if}
    </div>
    <fieldset>
      <div class="legend-container">
        <legend class:invalid={errorDate}>Pick a date</legend>
        {#if errorDate}
          <p id="error-date" class="error error--pick">{errorDateMsg}</p>
        {/if}
      </div>
      <div class="pick-container">
        <input class:invalid={errorDate} type="number" name="month" id="month" min="01" max="12" placeholder="MM" required>
        <input class:invalid={errorDate} type="number" name="day" id="day" min="01" max="31" placeholder="DD" required>
        <input class:invalid={errorDate} type="number" name="year" id="year" min="2022" max="2025" placeholder="YYYY" required>
      </div>
    </fieldset>
    <fieldset>
      <div class="legend-container">
        <legend class:invalid={errorTime}>Pick a time</legend>
        {#if errorTime}
         <p id="error-time" class="error error--pick">{errorTimeMsg}</p>
        {/if}
      </div>
      <div class="pick-container">
        <input class:invalid={errorTime} type="number" name="hour" id="hour" min="01" max="12" placeholder="09" required>
        <input class:invalid={errorTime} type="number" name="minute" id="minute" min="00" max="59" placeholder="00" required>
        <select>
          <option value="AM">AM</option>
          <option value="PM">PM</option>
        </select>
      </div>
    </fieldset>
    <NumPeople/>
    <button class="submit" type="submit">Make Reservation</button>
  </form>
</div>

<style>
  .pattern-wrap {
    transform: translateY(-8.5625rem);
  }

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
    box-shadow: 0rem 3rem 5rem -3.125rem rgba(0, 0, 0, .75);
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
    .pattern-wrap {
      transform: translateY(-14.375rem);
    }

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

  @media screen and (min-width: 71.875rem) {
    .pattern-wrap {
      transform: translateY(-21.375rem);
      position: relative;
      z-index: 1;
    }

    .pattern-wrap::before {
      content: url('/images/patterns/pattern-lines.svg');
      position: absolute;
      left: -5rem;
      bottom: -2.6875rem;
      z-index: -1;
    }
  }
</style>