<!-- This skipper helps people without access to a mouse to navigate the website. -->

<a href="#main-content">Ugrás a tartalomra</a>

<style>
  * {
    position: fixed;
    top: 0px;
    z-index: 1001;
    background-color: #000;
    color: #fff;
    padding: 5px;
    font-size: 1.2em;
    border-radius: 0 0 5px 5px;
    left: -1000px;
    transition: top 250ms;
  }
  *:focus {
    left: 15px;
  }
</style>
