<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anxiety Assessment</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="min-h-screen flex flex-col items-center bg-gray-100">

    <!-- Navigation -->
    <nav class="bg-white shadow-md py-4 px-6 flex justify-between items-center w-full">
        <a href="index.html" class="text-gray-700 font-semibold hover:text-blue-600">⬅ Back to Home</a>
    </nav>

    <!-- Assessment Form -->
    <div class="bg-white p-6 rounded-2xl shadow-lg max-w-xl mt-10">
        <h2 class="text-2xl font-bold text-center mb-6">Anxiety Assessment</h2>
        <form id="assessmentForm">
            
            <div class="mb-4">
                <p class="text-gray-700 font-semibold">1. How often do you feel anxious?</p>
                <div class="mt-2 space-y-2">
                    <label><input type="radio" name="q1" value="Never"> Never</label><br>
                    <label><input type="radio" name="q1" value="Sometimes"> Sometimes</label><br>
                    <label><input type="radio" name="q1" value="Often"> Often</label><br>
                    <label><input type="radio" name="q1" value="Always"> Always</label>
                </div>
            </div>

            <div class="mb-4">
                <p class="text-gray-700 font-semibold">2. Do you experience panic attacks?</p>
                <div class="mt-2 space-y-2">
                    <label><input type="radio" name="q2" value="Never"> Never</label><br>
                    <label><input type="radio" name="q2" value="Sometimes"> Sometimes</label><br>
                    <label><input type="radio" name="q2" value="Often"> Often</label><br>
                    <label><input type="radio" name="q2" value="Always"> Always</label>
                </div>
            </div>

            <div class="text-center mt-6">
                <button type="submit" class="bg-blue-600 text-white px-6 py-2 rounded-lg hover:bg-blue-700">Submit</button>
            </div>
        </form>

        <div id="result" class="mt-6 text-center font-semibold text-gray-700 hidden"></div>
    </div>

    <script>
        document.getElementById('assessmentForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent form submission
            
            let answers = [];
            const questions = ['q1', 'q2'];
            
            questions.forEach(q => {
                let selected = document.querySelector(`input[name="${q}"]:checked`);
                if (selected) {
                    answers.push(selected.value);
                }
            });

            if (answers.length < questions.length) {
                alert("Please answer all questions.");
                return;
            }

            let score = answers.filter(ans => ans === 'Often' || ans === 'Always').length;

            let resultText = "";
            if (score === 0) {
                resultText = "Your anxiety level seems low. Keep maintaining a healthy mindset!";
            } else if (score === 1) {
                resultText = "You might have mild anxiety. Consider relaxation techniques.";
            } else {
                resultText = "You may have moderate to high anxiety. Seeking professional help could be beneficial.";
            }

            document.getElementById('result').textContent = resultText;
            document.getElementById('result').classList.remove('hidden');
        });
    </script>

</body>
</html>
