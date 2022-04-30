<script>
  let people = "people"
  let number = 4
  
  function updatePeople() {
    if (this.id == "add") {
      number += 1;
    } else if (this.id == "subtract" && number === 1) {
      number == 1
    } else {
        number -=1;
      }

    (number === 1) ? people = "person" : people = "people";
  }
</script>

<div class="people">
  <h4 class="sr-only">Number of people</h4>
  <button type="button" id="subtract" class="people__control" aria-label="remove a person" on:click={updatePeople}>
    <img src="/images/icons/icon-minus.svg" alt="">
  </button>
  <p class="people__number">{number} {people}</p>
  <button type="button" id="add" class="people__control" aria-label="add a person" on:click={updatePeople}>
    <img src="/images/icons/icon-plus.svg" alt="">
  </button>
</div>

<style>
  .people {
    display: grid;
    grid-auto-flow: column;
    justify-content: space-between;
    border-bottom: 0.0625rem solid #8E8E8E;
    padding: 0rem 1.25rem 1rem;
    transition: border .5s ease;
    position: relative;
  }

  .people__number {
    font-weight: 700;
    font-size: 1.125rem;
    line-height: 1.556;
    letter-spacing: -0.0138rem;
  }

  @media screen and (min-width: 31.25rem) {
    .people {
      padding: 0rem 2rem 1rem;
    }
  }
</style>