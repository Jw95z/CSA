<!DOCTYPE html>
<html>
<head>
    <title>Calculator</title>
    
</head>
<body>
    <table border="1">
        <tr>
            <td colspan="4">
                <input type="text" id="a">
            </td>
        </tr>
        <tr>
            <td colspan="4">
                <input type="text" id="b">
            </td>
        </tr>
        <tr>
            <td colspan="3">AC</td>
            <td onclick="add('/')">/</td>
        </tr>
        <tr>
            <td onclick="add(7)">7</td>
            <td onclick="add(8)">8</td>
            <td onclick="add(9)">9</td>
            <td onclick="add('*')">*</td>
        </tr>
        <tr>
            <td onclick="add(4)">4</td>
            <td onclick="add(5)">5</td>
            <td onclick="add(6)">6</td>
            <td onclick="add('-')">-</td>
        </tr>
        <tr>
            <td onclick="add(1)">1</td>
            <td onclick="add(2)">2</td>
            <td onclick="add(3)">3</td>
            <td onclick="add('+')">+</td>
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