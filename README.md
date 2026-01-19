# full-stack-exp-1-24bda70178
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Admin Dashboard</title>

<style>
/* ---------- THEME VARIABLES ---------- */
:root {
  --bg-gradient: linear-gradient(135deg, #0f1c2e, #0a1320);
  --card-bg: rgba(255,255,255,0.07);
  --border-color: rgba(255,255,255,0.2);
  --text-color: #ffffff;
}

.light-theme {
  --bg-gradient: linear-gradient(135deg, #f4f6f8, #e8ebee);
  --card-bg: rgba(255,255,255,0.9);
  --border-color: rgba(0,0,0,0.15);
  --text-color: #000000;
}

/* ---------- BASE STYLES ---------- */
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family: Arial, sans-serif;
}

body{
  background: var(--bg-gradient);
  color: var(--text-color);
  height: 100vh;
}

/* ---------- GRID LAYOUT ---------- */
.dashboard{
  display:grid;
  grid-template-columns: 260px 1fr;
  grid-template-rows: 80px 1fr;
  grid-template-areas:
    "header header"
    "sidebar main";
  height:100vh;
}

/* ---------- HEADER ---------- */
header{
  grid-area: header;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding: 0 30px;
  background: var(--card-bg);
  border-bottom: 1px solid var(--border-color);
}

header h1{
  font-size: 28px;
}

/* ---------- TOGGLE BUTTON ---------- */
.toggle{
  background: var(--card-bg);
  border: 1px solid var(--border-color);
  padding: 10px 18px;
  border-radius: 12px;
  font-size: 16px;
  cursor: pointer;
  color: var(--text-color);
}

/* ---------- SIDEBAR ---------- */
aside{
  grid-area: sidebar;
  padding: 30px;
}

.sidebar-box{
  height:100%;
  border-radius: 20px;
  background: var(--card-bg);
  border: 1px solid var(--border-color);
  display:flex;
  align-items:center;
  justify-content:center;
  font-size: 22px;
}

/* ---------- MAIN CONTENT ---------- */
main{
  grid-area: main;
  padding: 30px;
}

.cards{
  display:grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

.card{
  height:150px;
  border-radius: 20px;
  background: var(--card-bg);
  border: 1px solid var(--border-color);
  display:flex;
  align-items:center;
  justify-content:center;
  font-size: 24px;
}
</style>
</head>

<body>

<div class="dashboard">
  <header>
    <h1>Admin Dashboard</h1>
    <button class="toggle" onclick="toggleTheme()">🌞 Light Mode</button>
  </header>

  <aside>
    <div class="sidebar-box">Navigation</div>
  </aside>

  <main>
    <div class="cards">
      <div class="card">Analytics</div>
      <div class="card">Users</div>
      <div class="card">Settings</div>
    </div>
  </main>
</div>

<script>
/* ---------- THEME SWITCHING ---------- */
const toggleBtn = document.querySelector('.toggle');

// Load saved theme
if(localStorage.getItem("theme") === "light"){
  document.body.classList.add("light-theme");
  toggleBtn.textContent = "🌙 Dark Mode";
}

// Toggle theme function
function toggleTheme(){
  document.body.classList.toggle("light-theme");

  if(document.body.classList.contains("light-theme")){
    localStorage.setItem("theme", "light");
    toggleBtn.textContent = "🌙 Dark Mode";
  } else {
    localStorage.setItem("theme", "dark");
    toggleBtn.textContent = "🌞 Light Mode";
  }
}
</script>

</body>
</html>
