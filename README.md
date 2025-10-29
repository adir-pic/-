[<!DOCTYPE html>
<html lang="he">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>טבלת חולצות</title>
<style>
    body {
        font-family: Arial, sans-serif;
        padding: 20px;
        background-color: #f5f5f5;
    }
    table {
        width: 100%;
        border-collapse: collapse;
        margin-bottom: 20px;
    }
    th, td {
        padding: 12px;
        text-align: center;
        border: 1px solid #ddd;
    }
    th {
        background-color: #004080;
        color: white;
    }
    td {
        background-color: #e0e0e0;
    }
    .btn {
        padding: 5px 12px;
        margin: 0 5px;
        font-size: 16px;
        cursor: pointer;
        border: none;
        border-radius: 5px;
        background-color: #004080;
        color: white;
    }
    .btn:active {
        background-color: #00264d;
    }
    .quantity {
        min-width: 40px;
        display: inline-block;
        text-align: center;
        font-weight: bold;
    }

    /* התאמה למובייל */
    @media (max-width: 600px) {
        table, th, td {
            font-size: 14px;
            padding: 8px;
        }
        .btn {
            padding: 3px 7px;
            font-size: 14px;
        }
    }
</style>
</head>
<body>

<h2>טבלת חולצות</h2>

<table>
    <thead>
        <tr>
            <th>צבע</th>
            <th>מידה</th>
            <th>כמות</th>
        </tr>
    </thead>
    <tbody>
        <!-- שורות הטבלה יווצרו אוטומטית -->
    </tbody>
</table>

<script>
const sizes = ["18", "20", "22", "24", "2XL", "3XL", "4XL"];
const tbody = document.querySelector("tbody");

sizes.forEach(size => {
    const tr = document.createElement("tr");

    // צבע
    const tdColor = document.createElement("td");
    tdColor.textContent = "כחול נייבי";
    tr.appendChild(tdColor);

    // מידה
    const tdSize = document.createElement("td");
    tdSize.textContent = size;
    tr.appendChild(tdSize);

    // כמות עם כפתורי פלוס/מינוס
    const tdQty = document.createElement("td");
    
    const minusBtn = document.createElement("button");
    minusBtn.textContent = "-";
    minusBtn.className = "btn";
    
    const qtySpan = document.createElement("span");
    qtySpan.textContent = "0";
    qtySpan.className = "quantity";

    const plusBtn = document.createElement("button");
    plusBtn.textContent = "+";
    plusBtn.className = "btn";

    minusBtn.addEventListener("click", () => {
        let current = parseInt(qtySpan.textContent);
        if(current > 0) qtySpan.textContent = current - 1;
        updateTotal();
    });

    plusBtn.addEventListener("click", () => {
        let current = parseInt(qtySpan.textContent);
        qtySpan.textContent = current + 1;
        updateTotal();
    });

    tdQty.appendChild(minusBtn);
    tdQty.appendChild(qtySpan);
    tdQty.appendChild(plusBtn);
    tr.appendChild(tdQty);

    tbody.appendChild(tr);
});

// הוספת ספירה כוללת של כל הכמויות
const totalDiv = document.createElement("div");
totalDiv.style.fontWeight = "bold";
totalDiv.style.marginTop = "20px";
totalDiv.textContent = "סה״כ חולצות: 0";
document.body.appendChild(totalDiv);

function updateTotal() {
    let total = 0;
    document.querySelectorAll(".quantity").forEach(span => {
        total += parseInt(span.textContent);
    });
    totalDiv.textContent = `סה״כ חולצות: ${total}`;
}
</script>

</body>
</html>
](https://github.com/adir-pic/-.git)
