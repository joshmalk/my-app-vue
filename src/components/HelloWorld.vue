<template>
    <div class="buttons">
    <button class="duplicate">Duplicate</button>
    <button class="modify">Modify Name</button>
    <button id="deletelastcard">Delete</button>
    <button id="changecolorbutton">Change Color</button>
    <button data-toggle-btn>Toggle Stats</button>
  </div>

  <div class="wrapper">
    <div class="container">
    <img class="image"
        src="https://media.gettyimages.com/id/1454029167/photo/cristiano-ronaldo-smiles-as-he-is-unveiled-as-an-al-nassr-player-at-mrsool-park-stadium-on.jpg?s=612x612&w=0&k=20&c=M3Gf2V64CamE0mD6gpeH9Qb3ohGEm2Ou5xc5ZH4fLmc="/>
    <div class="header">
      <h3>Cristiano Ronaldo</h3>
      <h4>Portuguese soccer player</h4>
    </div>
    <details class="details">
      <summary>Summary</summary>
      <div>
        <ul>
          <li>Five Time Ballon d'OR Winnder</li>
          <li>850 Career Goals</li>
          <li>Over 1,100 Career Appearances</li>
        </ul>
      </div>
      </details>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted() {
      const details = document.querySelector('summary');
      
      //Toggle Stats 
      document.querySelector('button[data-toggle-btn]').addEventListener('click', () => {
        if(details.parentNode.getAttribute('open')) {
          details.parentNode.removeAttribute('open');
        }
        else {
          details.parentNode.setAttribute('open','open');
        }
      });

      //Duplicate the 1st item/card
      document.querySelector('.duplicate').addEventListener('click', () => {
        const itemToClone = document.querySelector('.wrapper').cloneNode(true);
        document.body.appendChild(itemToClone);
      });

      //Modify name of 1st card
      document.querySelector('.modify').addEventListener('click', () => {
        let name = prompt("Give new name");
        if (name) {
          document.querySelector('.wrapper').querySelector('h3').innerText = name;
        }
      });

      //Delete last item/card
      document.querySelector('#deletelastcard').addEventListener('click', function() {
        const cards = document.querySelectorAll('.wrapper');
      // Check if there are cards to delete
        if (cards.length > 1) {
          const lastCard = cards[cards.length - 1];
          lastCard.parentNode.removeChild(lastCard);
        }
      });

      //Change color of 1st card
      document.querySelector('#changecolorbutton').addEventListener('click', () => {
        if(document.querySelector(".wrapper").style.background == "yellow") {
          document.querySelector(".wrapper").style.background = "blue";
        }
        else {
          document.querySelector(".wrapper").style.background = "yellow";
        }
      });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.wrapper {
  width: 400px;
  border: 2px solid black;
  display: inline-flex;
  background-color: orange;
}

.image {
  width: 400px;
}

.header {
  text-align: center;
  font-weight: bold;
  font-size: 2rem; 
}

.header h3:hover {
  font-style: italic;
  font-size: 1.1em;
}

.header h3,
.header h4 {
  transition: .3s ease-in-out all;
  margin: 16px;
  font-style: normal;
}

.buttons button:focus,
.buttons button:hover {
  background-color: rgba(200,0,50,.5);
}

.buttons button:active {
  background-color: rgba(50,0,200,.5);
}

.buttons {
  display: block;
}

button {
  padding: 12px;
  font-size: 32px;
}

.details {
  margin-left: 24px;
  padding: 10px;
}

.details summary { 
  font-size: 20px;
  font-weight: bold;
  
}

@media only screen and (max-width: 1200px){
  .wrapper {
    background-color: yellow;
  }
}
@media only screen and (max-width: 600px){
  .wrapper {
    background-color: blue;
  }
}
@media only screen and (max-width: 425px){
  .wrapper {
    font-weight: normal;
  }
  details {
    display: none;
  }
}
</style>
