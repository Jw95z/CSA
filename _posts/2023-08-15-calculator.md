---
toc: true
comments: true
layout: home
categories: [Week1]
---
<html>
<head>
    <title>Calculator</title>
    
</head>
<body>
<style>
body {
    display: grid;
}
td {
    border: 0px solid #ffebb5; 
    background-color: #ffebb5; 
    border-radius: 30px;
    box-shadow: inset 0 0 8px #deb13a;
    width: 40px; height: 40px;
    text-align: center;
    color: black;
    font-size: 40px
}
tr {
    background-color: blue;
    border-radius: 30%;
}
input {
    font-size: 60px;
    width: 600px;
    height: 60px;
    background-color: gold;
    color: red;
}
table {
    border: 0px;
}

</style>
    <table style="width:100%" >
        <tr>
            <td border-radius= "30px"  colspan="4">
                <input type="text" id="a">
            </td>
        </tr>
        <tr>
            <td border-radius= "30px" colspan="4">
                <input type="text" id="b">
            </td>
        </tr>
    </table>
    <table style="width:100%">
        <tr>
            <td border-radius= "30px" style="width:75%" colspan="3" onclick = "reset()">AC</td>
            <td border-radius= "30px" style="width:25%" onclick="add('/')">/</td>
        </tr>
        <tr style="width:100%">
            <td border-radius= "30px" style="width:25%" onclick="add(7)">7</td>
            <td border-radius= "30px" style="width:25%" onclick="add(8)">8</td>
            <td border-radius= "30px" style="width:25%" onclick="add(9)">9</td>
            <td border-radius= "30px" style="width:25%" onclick="add('*')">*</td>
        </tr>
        <tr>
            <td width="25%" onclick="add(4)">4</td>
            <td width="25%" onclick="add(5)">5</td>
            <td width="25%" onclick="add(6)">6</td>
            <td width="25%" onclick="add('-')">-</td>
        </tr>
        <tr>
            <td width="25%" onclick="add(1)">1</td>
            <td width="25%" onclick="add(2)">2</td>
            <td width="25%" onclick="add(3)">3</td>
            <td width="25%" onclick="add('+')">+</td>
        </tr>
        <tr>
            <td colspan="2" onclick="add(0)">0</td>
            <td onclick="add('.')">.</td>
            <td onclick="calculate()">=</td>
        </tr>
    </table>
    <script>
        function add(char) {
            var display = document.getElementById('a');
            display.value = display.value + char;
        }
        function calculate() {
            var display = document.getElementById('a');
            var result = eval(display.value); 
            document.getElementById('b').value = result;
        }
        function reset() {
            document.getElementById('a').value = "";
            document.getElementById('b').value = "";
        }
    </script>
</body>
</html>