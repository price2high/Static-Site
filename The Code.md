### We originally had a regular basic form and no styling. But once everything was done. When not add some color. 
---
### original index.html 
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Contact Us</title>
</head>
<body>
  <h1>Contact Us</h1>


  <form id="contactForm">
    <label>Name:</label>
    <input type="text" name="name" required><br>


    <label>Email:</label>
    <input type="email" name="email" required><br>


    <label>Message:</label>
    <textarea name="message" required></textarea><br>


    <button type="submit">Send</button>
  </form>


  <script src="script.js"></script>
</body>
</html>
```
---
### scripts.js
```
document.getElementById('contactForm').addEventListener('submit', async (e) => {
  e.preventDefault();


  const formData = {
    name: e.target.name.value,
    email: e.target.email.value,
    message: e.target.message.value
  };


  try {
    const response = await fetch('https://<your-api-gateway-id>.execute-api.<region>.amazonaws.com/prod/contact', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(formData)
    });


    if (response.ok) {
      alert('Message sent!');
    } else {
      alert('Error sending message.');
    }
  } catch (err) {
    console.error(err);
    alert('Network error.');
  }
});
```
---
![](https://github.com/price2high/Static-Sitepic/blob/main/Screenshot%202025-07-19%20122546.png)
---
# We wanted to add some flair, so we updated the index.html and the style.css.
### index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Contact Us</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
 
  <!-- Link to your external Barbie style file -->
  <link rel="stylesheet" href="style.css">
</head>
<body>


  <h1>💖 Contact Us 💖</h1>
 
  <form>
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>


    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>


    <label for="message">Message:</label>
    <textarea id="message" name="message" required></textarea>


    <button type="submit">💌 Send Message</button>
  </form>


</body>
</html>
```
---
### style.cs
```
/* Barbie Dream Contact Form */


body {
  background-color: #fff0f5;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #ff1493;
  margin: 0;
  padding: 30px;
}


h1 {
  text-align: center;
  font-size: 3em;
  color: #ff69b4;
  text-shadow: 1px 1px 3px #fff;
  margin-bottom: 30px;
}


form {
  max-width: 500px;
  margin: 0 auto;
  background-color: #ffffff;
  border: 2px solid #ff69b4;
  padding: 50px 40px; /* 🌸 Bigger inner spacing */
  border-radius: 20px;
  box-shadow: 0 4px 15px rgba(255, 105, 180, 0.4);
  box-sizing: border-box;
}


label {
  display: block;
  margin-top: 20px; /* 🌸 More space above each label */
  font-weight: bold;
  color: #d63384;
  font-size: 1.1em;
}


input[type="text"],
input[type="email"],
textarea {
  width: 100%;
  padding: 16px;              /* 🌸 Larger input padding */
  margin-top: 8px;
  margin-bottom: 20px;        /* 🌸 More spacing between inputs */
  border: 2px solid #ffb6c1;
  border-radius: 12px;
  font-size: 1.1em;
  background-color: #fffafc;
  color: #444;
  box-sizing: border-box;
}


textarea {
  resize: vertical;
  min-height: 150px;          /* 🌸 Larger text area */
}


button {
  background-color: #ff69b4;
  color: #fff;
  border: none;
  padding: 14px 28px;
  margin-top: 30px;
  font-size: 1.2em;
  font-weight: bold;
  border-radius: 15px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}


button:hover {
  background-color: #ff1493;
  transform: scale(1.05);
}


button:active {
  background-color: #e754a5;
  transform: scale(0.98);
}
```
---
![](https://github.com/price2high/Static-Sitepic/blob/main/Screenshot%202025-07-19%20154602.png)

---
# Lilac Theme :
### index.html 
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Contact Me</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="style.css">
</head>
<body>


  <h1>💜 Contact Me 💜</h1>


  <form>
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>


    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>


    <label for="message">Message:</label>
    <textarea id="message" name="message" required></textarea>


    <button type="submit">📨 Send Message</button>
  </form>


</body>
</html>
```
---
### lilac style.css
```
/* Soft Lilac Barbie Aesthetic */


body {
  background-color: #f8f4fc;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #6b4c9a;
  margin: 0;
  padding: 30px;
}


h1 {
  text-align: center;
  font-size: 3em;
  color: #a278e6;
  text-shadow: 1px 1px 3px #fff;
  margin-bottom: 30px;
}


form {
  max-width: 520px;
  margin: 0 auto;
  background-color: #ffffff;
  border: 2px solid #d8c1f5;
  padding: 50px 40px;
  border-radius: 20px;
  box-shadow: 0 6px 18px rgba(162, 120, 230, 0.2);
  box-sizing: border-box;
}


label {
  display: block;
  margin-top: 20px;
  font-weight: 600;
  color: #7a5ea8;
  font-size: 1.1em;
}


input[type="text"],
input[type="email"],
textarea {
  width: 100%;
  padding: 16px;
  margin-top: 8px;
  margin-bottom: 20px;
  border: 2px solid #e5d5f7;
  border-radius: 12px;
  font-size: 1.1em;
  background-color: #faf8ff;
  color: #333;
  box-sizing: border-box;
}


textarea {
  resize: vertical;
  min-height: 150px;
}


button {
  background-color: #b89cff;
  color: #fff;
  border: none;
  padding: 14px 28px;
  margin-top: 30px;
  font-size: 1.2em;
  font-weight: bold;
  border-radius: 15px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}


button:hover {
  background-color: #a278e6;
  transform: scale(1.05);
}


button:active {
  background-color: #9066d8;
  transform: scale(0.98);
```
---
![](https://github.com/price2high/Static-Sitepic/blob/main/Screenshot%202025-07-19%20134905.png)

---
# Seafoam Color
### index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Contact Us</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">


  <!-- Link to turquoise-themed stylesheet -->
  <link rel="stylesheet" href="style.css">
</head>
<body>


  <h1>Contact Us</h1>


  <form>
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>


    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>


    <label for="message">Message:</label>
    <textarea id="message" name="message" required></textarea>


    <button type="submit">Send Message</button>
  </form>


</body>
</html>
```
---
### style.css
```
/* Turquoise Contact Form */


body {
  background-color: #e0f7f7;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #007f7f;
  margin: 0;
  padding: 30px;
}


h1 {
  text-align: center;
  font-size: 3em;
  color: #20b2aa;
  text-shadow: 1px 1px 3px #ffffff;
  margin-bottom: 30px;
}


form {
  max-width: 500px;
  margin: 0 auto;
  background-color: #ffffff;
  border: 2px solid #20b2aa;
  padding: 50px 40px;
  border-radius: 20px;
  box-shadow: 0 4px 15px rgba(32, 178, 170, 0.3);
  box-sizing: border-box;
}


label {
  display: block;
  margin-top: 20px;
  font-weight: bold;
  color: #007f7f;
  font-size: 1.1em;
}


input[type="text"],
input[type="email"],
textarea {
  width: 100%;
  padding: 16px;
  margin-top: 8px;
  margin-bottom: 20px;
  border: 2px solid #a0e4e4;
  border-radius: 12px;
  font-size: 1.1em;
  background-color: #f0fdfd;
  color: #444;
  box-sizing: border-box;
}


textarea {
  resize: vertical;
  min-height: 150px;
}


button {
  background-color: #20b2aa;
  color: #fff;
  border: none;
  padding: 14px 28px;
  margin-top: 30px;
  font-size: 1.2em;
  font-weight: bold;
  border-radius: 15px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}


button:hover {
  background-color: #009e9e;
  transform: scale(1.05);
}


button:active {
  background-color: #007f7f;
  transform: scale(0.98);
}
```
---
![](https://github.com/price2high/Static-Sitepic/blob/main/Screenshot%202025-07-19%20155911.png)
---
![](https://github.com/price2high/Static-Sitepic/blob/main/Screenshot%202025-07-19%20160051.png)
---
## The Nav bar styling
This goes in style.css file
```
/* Navigation Bar */
nav {
  background-color: #d8c1f5; /* soft lilac background */
  padding: 12px;
  display: flex;
  justify-content: center;
  gap: 25px;
  border-radius: 0 0 12px 12px;
  box-shadow: 0 4px 12px rgba(162, 120, 230, 0.1);
  margin: -30px -30px 30px -30px; /* extend full width to edges */
}


nav a {
  color: #6b4c9a;
  text-decoration: none;
  font-weight: bold;
  font-size: 1.1em;
  padding: 6px 10px;
  border-radius: 8px;
  transition: background-color 0.3s ease, color 0.3s ease;
}


nav a:hover {
  background-color: #b89cff;
  color: #fff;
}
```
---
The Nav for each page: 
```
<nav>
  <a href="aboutme.html">Home</a>
  <a href="aboutme.html">About</a>
  <a href="projects.html">Projects</a>
  <a href="index.html">Contact</a>
</nav>
```
---
The code to add your picture to the about me page: 
``` <img src="me.jpg" alt="My Picture" class="profile-pic"> ```
