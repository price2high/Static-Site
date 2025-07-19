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
scripts.js
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
### We wanted to add some flair, so we updated the index.html and the style.css.
