<!DOCTYPE html>
<html>
<head>
  <title>Smart Construction System</title>
  <link rel="stylesheet" href="Rconst.css">
  <style>
    body {
      font-family: Arial;
      text-align: center;
      background: linear-gradient(to right, #4facfe, #00f2fe);
      color: white;
    }

    .container {
      margin-top: 50px;
    }

    input {
      padding: 10px;
      margin: 5px;
    }

    button {
      padding: 10px 20px;
      margin: 10px;
      background: orange;
      border: none;
      color: white;
      cursor: pointer;
    }

    #dashboard {
      display: none;
    }
  </style>
</head>

<body>

<div class="container">

  <!-- LOGIN -->
  <div id="login">
    <h2>🔐 Login</h2>
    <input type="text" id="username" placeholder="Username"><br>
    <input type="password" id="password" placeholder="Password"><br>
    <button onclick="login()">Login</button>
  </div>

  <!-- DASHBOARD -->
  <div id="dashboard">
    <h2>🏗️ Dashboard</h2>

    <input type="text" id="project" placeholder="Project Name">
    <input type="number" id="amount" placeholder="Amount">

    <button onclick="addProject()">Add Project</button>

    <h3>📊 Project List</h3>
    <ul id="list"></ul>

    <h3 id="total">Total: ₹0</h3>

    <button onclick="logout()">Logout</button>
  </div>

</div>

<script>
  let total = 0;

  function login() {
    let user = document.getElementById("username").value;
    let pass = document.getElementById("password").value;

    if(user === "admin" && pass === "1234") {
      document.getElementById("login").style.display = "none";
      document.getElementById("dashboard").style.display = "block";
    } else {
      alert("Wrong Login");
    }
  }

  function addProject() {
    let project = document.getElementById("project").value;
    let amount = parseInt(document.getElementById("amount").value);

    if(project === "" || isNaN(amount)) {
      alert("Enter valid data");
      return;
    }

    let list = document.getElementById("list");

    let li = document.createElement("li");
    li.innerText = project + " - ₹" + amount;

    list.appendChild(li);

    total += amount;
    document.getElementById("total").innerText = "Total: ₹" + total;

    // clear inputs
    document.getElementById("project").value = "";
    document.getElementById("amount").value = "";
  }

  function logout() {
    location.reload();
  }
 
</script>

</body>
</html>
