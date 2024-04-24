<template>
  <footer>
    <div>
      <div class="footer-title">Get to know Us</div>
      <ul>
        <li>Careers</li>
        <li>News Letter</li>
        <li>Sustainability</li>
        <li>Press Center</li>
      </ul>
    </div>
    <div>
      <div class="footer-title">Payment Products</div>
      <ul>
        <li>OSS Visa</li>
        <li>OSS Store Credit</li>
        <li>OSS Secured Card</li>
        <li>OSS Business Card</li>
        <li>Gifts Card</li>
      </ul>
    </div>
    <div>
      <div class="footer-title">Let Us Help You</div>
      <ul>
        <li>Your Account</li>
        <li>Your Orders</li>
        <li>Your Returns</li>
        <li>Shipping Rates</li>
        <li>Help</li>
      </ul>
    </div>
  </footer>
</template>
  
  <script>
export default {
  // Exporting Default Object
  name: "Footer",
};
</script>
  
<style scoped>
ul {
  list-style-type: none;
}

li {
  margin-bottom: 6px;
}

li:hover{
    cursor: pointer;
    text-decoration: underline;
    font-weight: bold;
}

footer {
  padding: 24px 0px;
  background-color: black;
  display: flex;
  width: 100%;
  color: white;
  justify-content: space-evenly;
  align-items: center;
}

.footer-title {
  font-weight: bold;
  font-size: larger;
  margin-bottom: 8px;
}
</style>