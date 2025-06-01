const PASSWORD = "Aksh123"; // Change this

function login() {
  const input = document.getElementById("password").value;
  if (input === PASSWORD) {
    const expiry = new Date().getTime() + 24 * 60 * 60 * 1000; // 24 hours
    localStorage.setItem("authToken", expiry);
    window.location.href = "index.html";
  } else {
    document.getElementById("error").innerText = "Incorrect Password!";
  }
}

function checkAuth() {
  const expiry = localStorage.getItem("authToken");
  if (!expiry || new Date().getTime() > expiry) {
    window.location.href = "login.html";
  }
}
