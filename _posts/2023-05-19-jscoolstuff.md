---
layout: base
search_exclude: true
image: images/logo.png
---

# Yo Yo Yo It's Rohan Gaikwad Yo in another year of AP CS

# Posts

<script>
        let score = 0
        let total = 0
        let count = 0
        let correct = 0
        class Jeopardy {
            constructor(question, answer, point) {
                this.question = question;
                this.answer = answer;
                this.point = point;
            }
            CheckAnswer(guess) {
                let answerfr = this.answer;
                return (guess.toUpperCase() === (answerfr).toUpperCase());
            }
        }
        let q1 = new Jeopardy('What is the capital of Chile?', 'Santiago', 2);
        let q2 = new Jeopardy('What is the capital of France?', 'Paris', 1);
        let q3 = new Jeopardy('What is the capital of Czech Republic?', 'Prague', 2);
        let q4 = new Jeopardy('What is the capital of Portugal?', 'Lisbon', 2);
        let q5 = new Jeopardy('What is the capital of Ethiopia?', 'Addis Ababa', 2);
        let q6 = new Jeopardy('Who is the President of the United States?', 'Joe Biden', 1);
        let q7 = new Jeopardy('Who is the leader of Russia? (Full Name)', 'Vladimir Putin', 1);
        let q8 = new Jeopardy('What is the capital of the United States? (No punctuation)', 'Washington DC', 1);
        let q9 = new Jeopardy('What country is being invaded by Russia?', 'Ukraine', 2);
    
            const qarray = [q1, q2, q3, q4, q5, q6, q7, q8, q9]

        function QNA(number) {
            if (number > qarray.length){
                document.getElementById('answer').innerHTML = "I can only print up to " + qarray.length + " questions";
            }
            for (let i = 0; i < number; i++) {
                const randomValue = qarray[Math.floor(Math.random() * qarray.length)];
                var index = qarray.indexOf(randomValue);
                if (index > -1) {
                    qarray.splice(index, 1);
                }
                let guess = prompt(randomValue.question + " Points: " + randomValue.point);
                count = count + 1;
                total = total + randomValue.point;
                if (randomValue.CheckAnswer(guess)) {
                    score = score + randomValue.point;
                    correct = correct + 1
                    document.getElementById('answer').innerHTML = "Well Done!";
                    document.getElementById('score').innerHTML = "Your score is " + score + "/" + total;
                    document.getElementById('correct').innerHTML = "You got " + correct + " questions correct out of " + count;
                }
                else {
                    document.getElementById('answer').innerHTML = "Nice Try!";
                    document.getElementById('score').innerHTML = "Your score is " + score + "/" + total;
                    document.getElementById('correct').innerHTML = "Sorry, you have gotten " + correct + " questions correct out of " + count;
                }
                }
        }
        function addQs(question, answer1, points) {
            let newquestion = new Jeopardy(question, answer1, parseInt(points));
            qarray.push(newquestion);
            console.log(qarray);
        }
    </script>
<html>
        <div class="container" style="position: absolute; font-size: 40px;color: red; left: 600px">
            <label for="number">How many questions do you want?</label>
            <br>
            <input id="number" type="number"/>
            <button onclick="QNA(document.getElementById('number').value)">Submit</button>
        </div>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <p style="text-align: center; font-size: 40px;color: red;" id="answer"></p>
        <p style="text-align: center; font-size: 40px;color: red;" id="score"></p>
        <p style="text-align: center; font-size: 40px;color: red;" id="correct"></p>
        <br>
        <br>
        <br>
        <div class="container" style = "position: absolute; font-size: 40px; color: red; left: 600px">
            <label for="question">Enter your own question</label>
            <br>
            <input id="question" type="text"/>
            <br>
            <input id="answer1" type="text"/>
            <br>
            <input id="points" type="number"/>
            <button onclick="addQs(document.getElementById('question').value, document.getElementById('answer1').value, document.getElementById('points').value)">Submit</button>
        <br>
        <br>
        <br><br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>





































