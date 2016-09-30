# Pascals-Triangle
In mathematics, Pascal's triangle is a triangular array of the binomial coefficients
<!DOCTYPE html>
<html>
<head>
	<title>Pascal-Triangle</title>
	<script src="js/Triangle.js"></script>
</head>
<body>
<p>Enter the number of rows in the triangle :</p>
<p><input type="text" id="num_rows" value="" /> <input type="button" onclick="dis()" value="Write table" /></p>
<hr />
Pascal's Triangle
<div id="triangle"></div>
<hr />
</body>
<script>
function factorial(p) {
    f = 1;
    for (i = 1; i <= p; i++) {
        f *= i;
    }
    return f;
}

function combinations(m, n) {
    if (n <= m) {
        var dividend1 = factorial(m);
        var divisor1 = factorial(m - n);
        var divisor = factorial(n);
        var dividend = dividend1 / divisor1;
        var combination = Math.round(dividend / divisor);
        return combination;
    } else return;
}

function table(rows) {
    var start = new Date().getTime();
    var rows = parseInt(rows);
    var text = "<table border='0' cellspacing='3'";
    text += " style='font-size:11px;font-family:verdana'>";
    var value = 0;
    var results = [];
    text += "<tr>";
    for (i = -1; i < rows; i++) {
        if (i == -1) text += "<td></td>";
        else text += "<td>N:" + i + "</td>";
    }
    text += "</tr>";
    for (m = 0; m < rows; m++) {
        text += "<tr>";
        for (n = 0; n < rows; n++) {
            if (n === 0) text += "<td>M:" + m + "</td>";
            text += "<td style='width:25;";
            text += "text-align:right;border:1px solid grey;padding:5px'>";
            if (n <= m) {
                value = combinations(m, n);
                text += value;
            } else text += "";
            text += "</td>";
        }
        text += "</tr>";
    }
    text += "</table>";
    document.getElementById('triangle').innerHTML = text;
    
}

function dis(){
    var rows = document.getElementById('num_rows').value;
    console.log(rows);
    return table(rows);    
}
</script>
</html>
Contact GitHub 
