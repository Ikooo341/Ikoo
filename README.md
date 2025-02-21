
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DAVAO UKAY UKAY BODEGAA</title>
</head>
<body>
    <h1>DAVAO UKAY UKAY BODEGA OFFICIAL WEBSITE</h1>
    <div>
        <h2>Register</h2>
        <input type="text" id="reg-name" placeholder="Name">
        <input type="email" id="reg-email" placeholder="Email">
        <input type="password" id="reg-password" placeholder="Password">
        <button onclick="register()">Register</button>
    </div>
    
    <div>
        <h2>Login</h2>
        <input type="email" id="login-email" placeholder="Email">
        <input type="password" id="login-password" placeholder="Password">
        <button onclick="login()">Login</button>
    </div>

    <div id="dashboard" style="display: none;">
        <h2>Dashboard</h2>
        <p id="user-info"></p>
        <input type="number" id="deposit-amount" placeholder="Deposit Amount">
        <button onclick="deposit()">Deposit</button>
        <input type="number" id="withdraw-amount" placeholder="Withdraw Amount">
        <button onclick="withdraw()">Withdraw</button>
    </div>

    <script>
        async function register() {
            const name = document.getElementById("reg-name").value;
            const email = document.getElementById("reg-email").value;
            const password = document.getElementById("reg-password").value;

            const res = await fetch("http://localhost:5000/register", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({ name, email, password })
            });
            alert(await res.json().message);
        }

        async function login() {
            const email = document.getElementById("login-email").value;
            const password = document.getElementById("login-password").value;

            const res = await fetch("http://localhost:5000/login", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({ email, password })
            });

            const data = await res.json();
            if (data.token) {
                localStorage.setItem("token", data.token);
                document.getElementById("dashboard").style.display = "block";
                document.getElementById("user-info").innerText = `Welcome, ${data.user.name}! Balance: $${data.user.balance}`;
            } else {
                alert(data.message);
            }
        }

        async function deposit() {
            const amount = parseFloat(document.getElementById("deposit-amount").value);
            const email = document.getElementById("login-email").value;

            const res = await fetch("http://localhost:5000/deposit", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({ email, amount })
            });

            alert(await res.json().message);
        }

        async function withdraw() {
            const amount = parseFloat(document.getElementById("withdraw-amount").value);
            const email = document.getElementById("login-email").value;

            const res = await fetch("http://localhost:5000/withdraw", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({ email, amount })
            });

            alert(await res.json().message);
        }
    </script>
</body>
</html>
