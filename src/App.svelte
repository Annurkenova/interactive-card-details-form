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

<body>
  <div class="container">
    <div class="card-image-front">
      <img src="/Oval_2.svg" class="card-image-1" alt="Front card" />
      <div class="card-details cardholder-name">{cardholderName}</div>
      <div class="card-details card-number">{cardNumber}</div>
      <div class="card-details exp-date">{expDate}</div>
      <div class="card-image-back">
        <img src="/bg-card-back.png" alt="back-card" />
        <span class="cvc">{cvc}</span>
      </div>
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
</body>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500&display=swap");

  :root {
    --Red: hsl(0, 100%, 66%);
    --White: hsl(0, 0%, 100%);
    --Light-grayish-violet: hsl(270, 3%, 87%);
    --Dark-grayish-violet: hsl(279, 6%, 55%);
    --Very-dark-violet: hsl(278, 68%, 11%);
  }
  *,
  * > * {
    font-family: "Space Grotesk", sans-serif;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  body {
    min-height: 100vh;
  }

  .container {
    display: flex;
    align-items: center;
  }

  .input-container {
    width: 45%;
    position: relative;
  }

  .card-image-front {
    width: 45%;
    position: relative;
  }

  .confirm-button {
    margin-top: 20px;
  }

  .card-details {
    position: absolute;
    font-size: 14px;
    color: #333;
  }

  .cardholder-name {
    top: 80px;
    left: 20px;
  }

  .card-number {
    top: 110px;
    left: 20px;
  }

  .exp-date {
    top: 150px;
    left: 20px;
  }

  .card-image-back {
    position: relative;
    width: 45%;
  }

  .card-image-back img {
    height: auto;
  }

  .cvc {
    top: 190px;
    left: 190px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 20px; /* Размер шрифта можно настроить по вашему вкусу */
    color: white; /* Цвет шрифта можно настроить по вашему вкусу */
  }
</style>
