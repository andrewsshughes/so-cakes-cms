<template>
  <div class="container page small">
    <h1>Drop Us A Message</h1>
    <form name="contact" netlify>
      <div>
        <label><span>Name:</span><input type="text" name="name" /></label>
      </div>
      <div>
        <label><span>Email:</span><input type="email" name="email" /></label>
      </div>
      <div>
        <label><span>Message:</span><textarea name="message"></textarea></label>
      </div>
      <div>
        <button type="submit">Send</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
form {
  margin-top: 41px;
}
form > div {
  margin-bottom: 20px;
}
form > div > label {
  display: flex;
  flex-direction: row;
}
form > div > label > * {
  flex-grow: 1;
  font-family: 'Lucidity';
}
form > div > label > input,
form > div > label > textarea {
  padding: 5px;
  border: 1px solid black;
}
form > div > label > textarea {
  height: 150px;
}
form > div > label > span {
  flex-basis: 90px;
  text-align: right;
  flex-grow: 0;
  margin-right: 15px;
}
form button {
  float: right;
  background: #ff66c4;
  border: none;
  color: white;
  padding: 2px 5px;
  font-family: 'Lucidity';
  border-radius: 3px;
  font-size: 18px;
}
form {
  width: 450px;
  margin-left: auto;
  margin-right: auto;
}
</style>