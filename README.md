# MEKI
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Questionnaire</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
    }
    .question {
      margin-bottom: 20px;
    }
    .submit-button {
      background-color: #4CAF50;
      color: white;
      border: none;
      padding: 10px 20px;
      cursor: pointer;
      font-size: 16px;
    }
    .submit-button:hover {
      background-color: #45a049;
    }
  </style>
</head>
<body>
  <h1>Questionnaire</h1>
  <form id="questionnaire">
    <div class="question">
      <p>1. What is your favorite color?</p>
      <label><input type="radio" name="question1" value="Red"> Red</label><br>
      <label><input type="radio" name="question1" value="Blue"> Blue</label><br>
      <label><input type="radio" name="question1" value="Green"> Green</label><br>
    </div>
    <div class="question">
      <p>2. What is your favorite animal?</p>
      <label><input type="radio" name="question2" value="Dog"> Dog</label><br>
      <label><input type="radio" name="question2" value="Cat"> Cat</label><br>
      <label><input type="radio" name="question2" value="Bird"> Bird</label><br>
    </div>
    <button type="button" class="submit-button" onclick="submitForm()">Submit</button>
  </form>

  <script src="https://cdn.emailjs.com/dist/email.min.js"></script>
  <script>
    // Initialize EmailJS
    (function() {
      emailjs.init("YOUR_EMAILJS_USER_ID"); // Replace with your EmailJS user ID
    })();

    function submitForm() {
      const form = document.getElementById('questionnaire');
      const formData = new FormData(form);
      const answers = {};
      for (const [key, value] of formData.entries()) {
        answers[key] = value;
      }

      // Send email using EmailJS
      emailjs.send("YOUR_SERVICE_ID", "YOUR_TEMPLATE_ID", answers)
        .then(() => {
          alert("Your responses have been sent successfully!");
        })
        .catch((error) => {
          console.error("Failed to send email:", error);
          alert("There was an error sending your responses. Please try again.");
        });
    }
  </script>
</body>
</html>