<script>
  let cardholderName = "";
  let cardNumber = "";
  let expDate = "";
  let cvc = "";

  function handleCardholderName(event) {
    cardholderName = event.target.value.replace(/[^a-zA-Z ]/g, "");
  }

  function handleCardNumber(event) {
    cardNumber = event.target.value
      .replace(/[^0-9a-zA-Z]/g, "")
      .replace(/(.{4})/g, "$1 ")
      .trim()
      .slice(0, 19);
  }

  function handleExpDate(event) {
    expDate = event.target.value
      .replace(/[^0-9]/g, "")
      .slice(0, 4)
      .replace(/(.{2})/, "$1/");
  }

  function handleCvc(event) {
    cvc = event.target.value.replace(/[^0-9]/g, "").slice(0, 3);
  }

  function confirmData() {
    alert(
      "Данные подтверждены: \n" +
        "Cardholder Name: " +
        cardholderName +
        "\n" +
        "Card Number: " +
        cardNumber +
        "\n" +
        "Exp. Date: " +
        expDate +
        "\n" +
        "CVC: " +
        cvc
    );
  }
</script>

<div class="container">
  <div class="card-image">
    <img src="/Oval_2.svg" class="card-image-1" alt="Front card" />
    <img src="/Group_13.svg" class="card-image-2" alt="Back card" />
  </div>

  <div class="input-container">
    <label for="cardholderName">Cardholder Name</label>
    <input
      type="text"
      id="cardholderName"
      bind:value={cardholderName}
      on:input={handleCardholderName}
    />

    <label for="cardNumber">Card Number</label>
    <input
      type="text"
      id="cardNumber"
      bind:value={cardNumber}
      on:input={handleCardNumber}
    />

    <label for="expDate">Exp. Date (MM/YY)</label>
    <input
      type="text"
      id="expDate"
      bind:value={expDate}
      on:input={handleExpDate}
    />

    <label for="cvc">CVC</label>
    <input type="text" id="cvc" bind:value={cvc} on:input={handleCvc} />

    <button on:click={confirmData} class="confirm-button">Confirm</button>
  </div>
</div>

<style>
  .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
  }

  .input-container {
    width: 45%;
  }

  .card-image {
    width: 45%;
  }

  .confirm-button {
    margin-top: 20px;
  }
</style>
