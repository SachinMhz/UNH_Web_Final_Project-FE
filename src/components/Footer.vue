<template>
  <footer class="footer">
    <div>
      <div class="footer-title">Get to know Us</div>
      <ul class="footer-list">
        <li class="footer-list-item">Careers</li>
        <li class="footer-list-item">News Letter</li>
        <li class="footer-list-item">Sustainability</li>
        <li class="footer-list-item">Press Center</li>
      </ul>
    </div>
    <div>
      <div class="footer-title">Payment Products</div>
      <ul class="footer-list">
        <li class="footer-list-item">OSS Visa</li>
        <li class="footer-list-item">OSS Store Credit</li>
        <li class="footer-list-item">OSS Secured Card</li>
        <li class="footer-list-item">OSS Business Card</li>
        <li class="footer-list-item">Gifts Card</li>
      </ul>
    </div>
    <div>
      <div class="footer-title">Let Us Help You</div>
      <ul class="footer-list">
        <li class="footer-list-item">Your Account</li>
        <li class="footer-list-item">Your Orders</li>
        <li class="footer-list-item">Your Returns</li>
        <li class="footer-list-item">Shipping Rates</li>
        <li class="footer-list-item">Help</li>
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
.footer-list {
  list-style-type: none;
}

.footer-list-item {
  margin-bottom: 6px;
}

.footer-list-item:hover{
    cursor: pointer;
    text-decoration: underline;
    font-weight: bold;
}

.footer {
  padding: 24px 0px;
  background-color: black;
  display: flex;
  width: 100%;
  color: white;
  justify-content: space-evenly;
}

.footer-title {
  font-weight: bold;
  font-size: larger;
  margin-bottom: 8px;
}

@media only screen and (max-width: 700px) {
  .footer {
    flex-direction: column;
    text-align: center;
  }

  .footer-title{
    margin-top: 24px;
  }
}
</style>