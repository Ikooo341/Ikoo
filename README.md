<!-- PROGRAMMED BY Ikoo_ -->

<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #FAEEE6;
        }
        #content {
            border: 1px solid transparent;
            background-color: #FFC0CB;
            border-radius: 12px;
            box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
            padding: 20px;
            text-align: center;
        }
        #yesButton, #noButton {
            font-size: 20px;
            border-radius: 12px;
            box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
            transition: 0.3s;
            padding: 15px;
            border: none;
            cursor: pointer;
            margin: 10px;
        }
        #yesButton {
            background-color: #4CAF50; /* Green */
            color: white;
        }
        #noButton {
            background-color: #f44336; /* Red */
            color: white;
        }
        #noButton:disabled {
            background-color: #ddd;
            color: #666;
            box-shadow: none;
        }
        #yesButton:hover, #noButton:hover {
            box-shadow: 0 12px 20px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
        }

        .heart {
            position: fixed;
            top: -100px;
            width: 100px;
            height: 100px;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 29.6"><path fill="%23FF0000" d="M16 29.6c-1-.6-21-12.6-16-20C5.7 5.6 10.3 4 16 11c5.7-7 10.3-5.4 16-2.6 5 7.4-15 19.6-16 20z"/></svg>');
            animation: fall 4s linear infinite;     /* W3SCHOOL ANIMATION NG HEART */
        }

        @keyframes fall {
            0% { transform: translateY(-100vh); }
            100% { transform: translateY(100vh); }
        }

    </style>
</head>
<body>
    <div id="content">
        <h2 id="question">Pwede kaba maging girlfriend ko?</h2>
        <button id="yesButton">YES</button>
        <button id="noButton">NO</button>
        <p id="message"></p>
    </div>

    <script>
        var noClickCount = 0;
        document.getElementById('noButton').addEventListener('click', function() { //NOOOOO button
            noClickCount++;
            if (noClickCount == 1) {
                document.getElementById('yesButton').style.fontSize = '30px';
            } else if (noClickCount == 2) {
                this.style.fontSize = '10px';
                document.getElementById('yesButton').style.fontSize = '40px';
            } else if (noClickCount == 3) {
                document.getElementById('yesButton').style.fontSize = '90px';
                this.style.fontSize = '7px';
            } else if (noClickCount == 4) {
                this.style.position = 'absolute';
                this.style.left = Math.random() * window.innerWidth + 'px';
                this.style.top = Math.random() * window.innerHeight + 'px';
            } else if (noClickCount >= 5 && noClickCount < 10) {
                this.style.position = 'absolute';
                this.style.left = Math.random() * window.innerWidth + 'px';
                this.style.top = Math.random() * window.innerHeight + 'px';
            } else if (noClickCount >= 10 && noClickCount < 15) {
                // Avoid disabling the button
                // this.disabled = true;
                this.style.position = 'absolute';
                this.style.left = Math.random() * window.innerWidth + 'px';
                this.style.top = Math.random() * window.innerHeight + 'px';
                document.getElementById('message').innerText = 'Are you sure?';
                document.getElementById('message').style.position = 'absolute';
                document.getElementById('message').style.left = this.style.left;
                document.getElementById('message').style.top = parseFloat(this.style.top) + 50 + 'px';
            } else if (noClickCount == 15) {
                document.getElementById('message').innerText = 'Oh No! You broke the button :c';
                this.disabled = true;
                this.style.color = grey;
                document.getElementById('message').innerText = 'Oh No! You broke the button :c';
            }
        });

        document.getElementById('yesButton').addEventListener('click', function() {                 //YESSSS button
            document.getElementById('question').innerText = 'yiee ilove you soo much';
            for (var i = 0; i < 100; i++) {
                var heart = document.createElement('div');
                heart.className = 'heart';
                heart.style.left = Math.random() * window.innerWidth + 'px';
                heart.style.animationDuration = Math.random() * 2 + 3 + 's'; //between 3 and 5 secs
                heart.style.animationDelay = Math.random() * 2 + 's'; // eto 0 and 2. di ko sure kung sure na
                document.body.appendChild(heart);
            }
            document.getElementById('yesButton').style.display = 'none';
            document.getElementById('noButton').style.display = 'none';
        });
    </script>
</body>
</html>