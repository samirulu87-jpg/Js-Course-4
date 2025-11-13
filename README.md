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
     inputField.value = "";  
});

/*challenge 3*/
const addbtn = document.getElementById("adding");  //Adds an addition button
const subbtn = document.getElementById("subtracting");  //Adds a subtraction button
const multiebtn = document.getElementById("Multiply");  //Adds a multiplication button
const dividebtn = document.getElementById("Divide");  //Adds a divition button


const firstnum = document.getElementById("First-num");
const secondnum = document.getElementById("Second-num");

const addoutput = document.getElementById("addoutput");
const suboutput = document.getElementById("suboutput");
const multiplyoutput = document.getElementById("multiplyoutput");
const divideoutput = document.getElementById("divitionoutput");

addbtn.addEventListener("click", function() { //Adds event listener for if the add button is pressed, function will run after it is pressed
    const num1 = Number(firstnum.value);
    const num2 = Number(secondnum.value);
    addoutput.textContent = num1 + num2;
});

subbtn.addEventListener("click", function() {  //Adds event listener for if the subtract button is pressed, function will run after it is pressed
    const num1 = Number(firstnum.value);
    const num2 = Number(secondnum.value);
    suboutput.textContent = num1 - num2;
});

multiebtn.addEventListener("click", function() {  //Adds event listener for if the multiplication button is pressed, then the function will run
    const num1 = Number(firstnum.value);
    const num2 = Number(secondnum.value);
    multiplyoutput.textContent = num1 * num2;
});
dividebtn.addEventListener("click", function() {  //Adds event listener for if the divition button is pressed, then the function will run
    const num1 = Number(firstnum.value);
    const num2 = Number(secondnum.value);
    divideoutput.textContent = num1 / num2;
});

/*Challenge 4*/
const imgback = document.getElementById("imgback")  //Adds image back button
const imgnext = document.getElementById("imgnext")  //Adds image next button
const imageslide = document.getElementById("imageslide")  //Adds image slide
const imagesForPage = ["images/dog&cat.jpg", "images/cutedog3.jpg", "images/dogimg2.webp"] //Images in the array for what images can be used
let currentIndex = 0;

function updateImage() {  //Will update the image based on what button is pressed
    imageslide.src = imagesForPage[currentIndex]
}

imgnext.addEventListener("click", () => {  //Adds an event listener for the imagenext button
    currentIndex++ 
    if (currentIndex >= imagesForPage.length) {
        currentIndex = 0;
    }
    updateImage();
});

    imgback.addEventListener("click", () => {  //Adds an event listener for the imageback button
      currentIndex--;
      if (currentIndex < 0) {
        currentIndex = imagesForPage.length - 1;
      }
      updateImage();
    });

/* Challenge 5 */
const emailInput = document.getElementById("email");   //Specifies what kind of input it is- email
const passwordInput = document.getElementById("password");   //Specifies what kind of input it is-password
const submitBtn = document.getElementById("emailsubmit");  //Adds sumbit button for the input fields

submitBtn.addEventListener("click", () => {
  const email = emailInput.value.trim();
  const password = passwordInput.value.trim();

  const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

  if (!emailPattern.test(email)) {  //If email input is not valid, you get an alert
    alert("Please enter a valid email address.");
    return;
  }

  if (password.length < 6) {  //If password length is not long enough, you get an alert
    alert("Password must be at least 6 characters long.");
    return;
  }

  alert("✅ Email and password are valid!");  //When both inputs are valid an submitted, you get an alert
});
