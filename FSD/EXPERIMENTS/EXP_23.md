# Lab Cycle – Experiment 23

## Aim:

Build a webpage that demonstrates handling the following JavaScript events:

- `onclick`
- `onmouseover`
- `onkeyup`
- `onfocus`

***

***

## Source Code

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Event Handling Lab</title>

    <style>
        /* Simple Box */
        .box {
            width: 200px;
            height: 100px;
            background-color: lightblue;
            border: 1px solid black;
            text-align: center;
            line-height: 100px;
            margin-bottom: 20px;
        }
    </style>

    <script>
        // onclick event
        function buttonClick() {
            alert("Button Clicked!");
        }

        // onmouseover event
        function mouseOver() {
            var box = document.getElementById("colorBox");
            box.style.backgroundColor = "red";
            box.innerText = "Mouse Over";
        }

        // onmouseout event
        function mouseOut() {
            var box = document.getElementById("colorBox");
            box.style.backgroundColor = "lightblue";
            box.innerText = "Hover Me";
        }

        // onkeyup event
        function keyUpEvent() {
            var inputText = document.getElementById("typeInput").value;
            document.getElementById("keyMessage").innerText =
                "You typed: " + inputText;
        }

        // onfocus event
        function focusEvent() {
            var input = document.getElementById("focusInput");
            input.style.backgroundColor = "beige";
            document.getElementById("focusMessage").innerText =
                "Input box focused!";
        }
    </script>
</head>

<body>

    <h2>Event Handling Lab Program</h2>

    <!-- onclick -->
    <button onclick="buttonClick()">Click Me</button>

    <br><br>

    <!-- onmouseover -->
    <div class="box"
         id="colorBox"
         onmouseover="mouseOver()"
         onmouseout="mouseOut()">
        Hover Me
    </div>

    <!-- onkeyup -->
    <label>Type Something:</label><br>
    <input type="text" id="typeInput" onkeyup="keyUpEvent()">
    <p id="keyMessage"></p>

    <!-- onfocus -->
    <label>Focus Input:</label><br>
    <input type="text" id="focusInput" onfocus="focusEvent()">
    <p id="focusMessage"></p>

</body>
</html>
```


***

## Explanation

- The **`onclick`** event on the button calls `buttonClick()`, which displays an alert saying “Button Clicked!”.
- The **`onmouseover`** and **`onmouseout`** events on the box change its background color and text when the mouse enters and leaves the box.
- The **`onkeyup`** event on the first text input calls `keyUpEvent()`, which shows the text typed by the user in the paragraph below.
- The **`onfocus`** event on the second text input calls `focusEvent()`, which changes the input background to beige and displays “Input box focused!” below it.

