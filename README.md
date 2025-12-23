<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For Jihan 💖</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
    margin: 0;
    font-family: "Poppins", sans-serif;
    overflow: hidden;
}

/* ---------- LOGIN ---------- */
.login {
    height: 100vh;
    background: white;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.login input {
    padding: 12px;
    width: 220px;
    border-radius: 20px;
    border: 1px solid #ccc;
    text-align: center;
    margin-bottom: 15px;
}

.login button {
    padding: 10px 30px;
    border-radius: 20px;
    border: none;
    background: #f3a6b8;
    color: white;
    font-size: 16px;
    cursor: pointer;
}

/* ---------- HEART PAGE ---------- */
.heart-page {
    display: none;
    height: 100vh;
    background: #f4e3dc;
    position: relative;
}

.guide {
    position: absolute;
    top: 45%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    color: #a56a6a;
}

.line {
    width: 2px;
    height: 60px;
    background: #a56a6a;
    margin: 10px auto;
}

.heart {
    font-size: 42px;
    cursor: pointer;
    animation: pulse 1.5s infinite;
}

@keyframes pulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.3); }
    100% { transform: scale(1); }
}

/* ---------- FLOATING HEARTS ---------- */
.floating-heart {
    position: absolute;
    bottom: -10%;
    font-size: 18px;
    animation: floatUp 6s linear infinite;
    opacity: 0.8;
}

@keyframes floatUp {
    from { transform: translateY(0); opacity: 1; }
    to { transform: translateY(-120vh); opacity: 0; }
}

/* ---------- FINAL PAGE ---------- */
.final {
    display: none;
    height: 100vh;
    background: #f4e3dc;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 40px;
}

/* TEXT LEFT */
.message {
    width: 45%;
    font-size: 20px;
    color: #6b3f3f;
    line-height: 1.6;
    white-space: pre-line;
}

/* ROSE RIGHT */
.rose {
    width: 45%;
    display: flex;
    justify-content: center;
}

svg {
    width: 260px;
}

/* DRAWING ANIMATION */
path {
