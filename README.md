Link to the site ------

This is the Js script and the notes attached for easy access to relivent code 

/*challenge 1*/
const colors = ["#E4080A", "#FE9900", "#FED530", "#5CE028", "#5DE2E7" ,"#060270", "#600273", "#AF3F8A", "#040404", "#bd901dff", "#8d7de9ff", "#713a49ff" , "#824741ff", "#689b6dff"
, "#e0c728ff", "#034c54ff"];/*This line creates an array containing all the colors that will be used later*/
const buttoncolor = document.getElementById("colorbtn"); /*Pulls the corasponding button from the htlm page*/

buttoncolor.addEventListener("click", () => { /*creates a function based on if the defined button before has been clicked*/
    const randomColorIndex = colors[Math.floor(Math.random()*colors.length)]; /*sets the random pattern of the colors to be used later*/
    document.body.style.backgroundColor = randomColorIndex; /*sets the background to that set random color*/

    const allButtons = document.querySelectorAll("button"); /*Selects all the buttons on the html page*/
  allButtons.forEach(btn => { /*This selects the buttons to be changed*/
    btn.style.backgroundColor = randomColorIndex; /*Changes the background of the buttons to match the random color of the html page*/
    btn.style.color = getContrastColor(randomColorIndex);/*This applies the function later defined to change if the button text needs to be black or white*/
});
});
function getContrastColor(hex) { /*Function to determine if text is black or white*/
  const c = hex.substring(1);
  const rgb = parseInt(c, 16);
  const r = (rgb >> 16) & 0xff;
  const g = (rgb >> 8) & 0xff;
  const b = rgb & 0xff;
  const brightness = (r * 299 + g * 587 + b * 114) / 1000;
  return brightness > 150 ? "#000" : "#fff";
}



/*challenge 2*/
const guessbtn = document.getElementById("guessbtn");
guessbtn.addEventListener("click", function() {  //Adds even listener for when the button is clicked, funtion will take place when button is clicked
    const personGuess = Number(document.getElementById("guess-number").value)  //Takes input from the user
    const inputField = document.getElementById("guess-number");
    const inputValue = inputField.value.trim();

     if (inputValue === "") { //If the input is blank and the submission button is presses, an alery will pop up
        alert("Please enter a number!");
        return;
    }

    const puterNumber = Math.floor(Math.random()* 10)+ 1; //Randomizes the number being guessed
    if 
        (personGuess === puterNumber) { //Output if the user guesses the right/wrong number
        document.getElementById("numoutput").textContent = `Congradulations you Guessed Correctly! The number was ${puterNumber}!`;
    } else { 
        document.getElementById("numoutput").textContent = `Nice try, but thats not quite right! The number was ${puterNumber}!`;;  
    }
     in
