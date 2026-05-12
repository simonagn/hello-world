<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>
        body { font-family: sans-serif; padding: 20px; line-height: 1.6; background: #f4f4f9; }
        .card { background: white; padding: 20px; border-radius: 10px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); margin-bottom: 20px; }
        input { padding: 10px; width: 80%; border: 1px solid #ccc; border-radius: 5px; }
        button { padding: 10px 20px; background: #28a745; color: white; border: none; border-radius: 5px; cursor: pointer; }
        .feedback { margin-top: 10px; font-weight: bold; }
        .correct { color: green; }
        .wrong { color: red; }
    </style>
</head>
<body>

    <h1>📝 Quick Revision Quiz</h1>
    <p>Type your answer and click check!</p>

    <div class="card">
        <p>1. If I ____ (win) the lottery tomorrow, I would buy a house. (2nd Conditional)</p>
        <input type="text" id="q1" placeholder="Type here...">
        <button onclick="check('q1', 'won')">Check</button>
        <div id="q1-ref" class="feedback"></div>
    </div>
