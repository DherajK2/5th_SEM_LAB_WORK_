# Lab Cycle – Experiment 4

## Aim:

Write a JavaScript program that demonstrates handling events from different HTML elements to:

1. Trigger an alert when the user clicks anywhere on the body of the page.
2. Change the text of a button when it is clicked and display a success message below the button.
3. Dynamically update a paragraph with the text entered in a text box as the user types.
4. Display a password strength message (Weak, Medium, or Strong) based on the length of the entered password, updating the message as the user types.

***

***

## Source Code

```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Event Handling Example</title>
</head>

<body style="padding: 20px;">

    <h2>JavaScript Event Handling Example</h2>

    <!-- Button for click event -->
    <button id="myButton">Click Me</button>
    <p id="successMsg"></p>

    <br><br>

    <!-- Text input for live typing -->
    <label>Type Something: </label>
    <input type="text" id="textInput">
    <p id="displayPara"></p>

    <br>

    <!-- Password input for strength check -->
    <label>Enter Password: </label>
    <input type="password" id="passwordInput">
    <p id="passwordStrength"></p>

    <script>
        /* ----------------------------------------------------
           1. Body onclick event
           Purpose: Show an alert when user clicks anywhere
           on the page.
        ---------------------------------------------------- */
        document.body.onclick = function () {
            alert("You clicked on the page!");
        };

        /* ----------------------------------------------------
           2. Button onclick event
           Purpose:
           - Change button text when clicked
           - Display success message below the button
        ---------------------------------------------------- */
        document.getElementById("myButton").onclick = function (event) {
            // Stop the click from bubbling to body (to avoid extra alert)
            event.stopPropagation();
            this.innerText = "Clicked!";
            document.getElementById("successMsg").innerText =
                "Button clicked successfully!";
        };

        /* ----------------------------------------------------
           3. Textbox oninput event
           Purpose: Update paragraph with whatever the user types
           in the text box, in real-time.
        ---------------------------------------------------- */
        document.getElementById("textInput").oninput = function () {
            document.getElementById("displayPara").innerText =
                "You typed: " + this.value;
        };

        /* ----------------------------------------------------
           4. Password oninput event
           Purpose: Check the length of the password and show
           strength as Weak / Medium / Strong.
        ---------------------------------------------------- */
        document.getElementById("passwordInput").oninput = function () {
            let password = this.value;
            let strength = "";

            if (password.length < 4) {
                strength = "Password Strength: Weak";
            } else if (password.length < 8) {
                strength = "Password Strength: Medium";
            } else {
                strength = "Password Strength: Strong";
            }

            document.getElementById("passwordStrength").innerText = strength;
        };
    </script>

</body>
</html>
```


***

## Output

- Initial page with button, text box, and password field.
- After clicking the button: text changes to “Clicked!” and success message appears.
- When clicking anywhere on the body, an alert box appears.
- While typing in the text box, the paragraph below shows “You typed: …”.
- Password field showing Weak / Medium / Strong based on length.

***

## Explanation

- The `onclick` handler on `document.body` detects any click on the page and shows an alert to demonstrate page-level event handling.
- The button’s `onclick` handler changes its own label using `this.innerText` and sets a success message, while `event.stopPropagation()` prevents the body click handler from also firing.
- The text box uses the `oninput` event so that every character typed (or deleted) immediately updates the paragraph with the current value.
- The password field also uses `oninput`, checks `password.length`, and categorizes the strength into Weak, Medium, or Strong, updating the message dynamically as the user types.

***

## Viva Questions

1. **What is the difference between `onclick` and `oninput` events?**
2. **Why is `event.stopPropagation()` used in the button click handler?**
3. **How can you change the text of an HTML element using JavaScript?**
4. **Why is `oninput` better than `onchange` for real-time password strength checking?**
5. **How would you extend this example to check for special characters or numbers in the password for a more accurate strength check?**
<span style="display:none">[^1][^2][^3][^4][^5][^6][^7]</span>

<div align="center">⁂</div>

[^1]: EXP_4.1.jpg

[^2]: EXP_4.3.jpg

[^3]: EXP_4.2.jpg

[^4]: EXP_4.4.jpg

[^5]: EXP_4.5.jpg

[^6]: EXP_4.6.jpg

[^7]: EXP_4.7.jpg

