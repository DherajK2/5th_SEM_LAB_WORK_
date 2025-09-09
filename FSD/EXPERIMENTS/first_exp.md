# Lab Cycle - Experiment 1

## Aim:
Create the below registration form using forms in HTML.

## Output Design:

![Form Design](form.png)

## HTML Code:

```html
<!DOCTYPE html>
<html>
<head>
    <title>User Information Form</title>
</head>
<body>
    <form>
        <h2>User Information Form</h2>

        <label for="name">Name</label>
        <input type="text" id="name" name="name" required><br><br>

        <label for="email">Email</label>
        <input type="email" id="email" name="email" required><br><br>

        <label for="age">Age</label>
        <input type="number" id="age" name="age" required><br><br>

        <label for="country">Country</label>
        <select id="country" name="country" required>
            <option value="">--Select Country--</option>
            <option value="India">India</option>
            <option value="USA">USA</option>
            <option value="UK">UK</option>
        </select><br><br>

        <label for="password">Password</label>
        <input type="password" id="password" name="password" required><br><br>

        <!-- PDF Upload -->
        <label for="pdfUpload">Resume</label>
        <input type="file" id="pdfUpload" name="pdfUpload" accept="application/pdf" required><br><br>

        <label>Hobbies</label>
        <input type="checkbox" name="hobbies" value="cricket" required>Cricket
        <input type="checkbox" name="hobbies" value="football">Football<br><br>

        <label>Gender</label>
        <input type="radio" name="gender" value="male" required>Male
        <input type="radio" name="gender" value="female" required>Female<br><br>

        <label for="city">City</label>
        <select id="city" name="city" required>
            <option value="">--Choose city--</option>
            <option value="Mysuru">Mysuru</option>
            <option value="Bengaluru">Bengaluru</option>
            <option value="Mandya">Mandya</option>
        </select><br><br>

        <label for="address">Address</label><br>
        <textarea id="address" name="address" rows="4" cols="40" required></textarea><br><br>

        <input type="submit" value="Submit">
        <input type="reset" value="Reset">
    </form>
</body>
</html>
```
## HTML Modification Code:
### Add images, multiple file format, Multiple files at once (For Viva)

```html
<!DOCTYPE html>
<html>
<head>
    <title>User Information Form</title>
</head>
<body>
    <form>
        <h2>User Information Form</h2>

        <label for="name">Name</label>
        <input type="text" id="name" name="name" required><br><br>

        <label for="email">Email</label>
        <input type="email" id="email" name="email" required><br><br>

        <label for="age">Age</label>
        <input type="number" id="age" name="age" required><br><br>

        <label for="country">Country</label>
        <select id="country" name="country" required>
            <option value="">--Select Country--</option>
            <option value="India">India</option>
            <option value="USA">USA</option>
            <option value="UK">UK</option>
        </select><br><br>

        <label for="password">Password</label>
        <input type="password" id="password" name="password" required><br><br>

        <!-- PDF Upload -->
        <label for="pdfUpload">Resume</label>
        <input type="file" id="pdfUpload" name="pdfUpload" accept="application/pdf" required><br><br>

        <!-- Single Image Upload -->
        <label for="singleImage">Upload Image</label>
        <input type="file" id="singleImage" name="singleImage" accept="image/*" required><br><br>

        <!-- Document Upload -->
        <label for="documentUpload">Choose a Document (Word, PDF, etc.)</label>
        <input type="file" id="documentUpload" name="documentUpload" accept=".pdf,.doc,.docx,.txt" required><br><br>

        <!-- Multiple File Types -->
        <label for="multipleFiles">Choose Multiple File Types (PDF, DOCX, Images)</label>
        <input type="file" id="multipleFiles" name="multipleFiles[]" accept=".pdf,.doc,.docx,image/*" multiple required><br><br>

        <label>Hobbies</label>
        <input type="checkbox" name="hobbies" value="cricket" required>Cricket
        <input type="checkbox" name="hobbies" value="football">Football<br><br>

        <label>Gender</label>
        <input type="radio" name="gender" value="male" required>Male
        <input type="radio" name="gender" value="female" required>Female<br><br>

        <label for="city">City</label>
        <select id="city" name="city" required>
            <option value="">--Choose city--</option>
            <option value="Mysuru">Mysuru</option>
            <option value="Bengaluru">Bengaluru</option>
            <option value="Mandya">Mandya</option>
        </select><br><br>

        <label for="address">Address</label><br>
        <textarea id="address" name="address" rows="4" cols="40" required></textarea><br><br>

        <input type="submit" value="Submit">
        <input type="reset" value="Reset">
    </form>
</body>
</html>
```
