<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Internal Undertaking & Return Note</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
    body{
        font-family: Arial, sans-serif;
        background:#f4f4f4;
        margin:0;
        padding:0;
    }

    .container{
        max-width:900px;
        background:#fff;
        padding:20px;
        margin:20px auto;
        border-radius:8px;
        box-shadow:0 0 10px rgba(0,0,0,0.1);
    }

    h1,h2,h3{
        color:#08327f;
        border-bottom:2px solid #08327f;
        padding-bottom:5px;
    }

    label{
        font-weight:bold;
        margin-top:10px;
        display:block;
    }

    input, select, textarea{
        width:100%;
        padding:8px;
        margin-top:5px;
        border-radius:4px;
        border:1px solid #ccc;
    }

    table{
        width:100%;
        border-collapse:collapse;
        margin-top:10px;
    }

    table th, td{
        border:1px solid #ddd;
        padding:8px;
        font-size:14px;
        text-align:left;
    }

    table th{
        background:#08327f;
        color:#fff;
    }

    button{
        margin-top:12px;
        padding:10px 15px;
        background:#08327f;
        color:#fff;
        border:none;
        border-radius:4px;
        font-weight:bold;
        cursor:pointer;
    }

    button:hover{
        background:#051d4d;
    }

    .thankyou{
        text-align:center;
        padding:40px;
        display:none;
        color:#08327f;
    }

</style>
</head>
<body>

<div class="container" id="formContainer">

    <h1>Internal Undertaking & Return Note</h1>

    <h3>Personnel Details</h3>

    <label>Name</label>
    <input type="text" required>

    <label>MSO No. / E-Pass No.</label>
    <input type="text">

    <label>Project / Department</label>
    <input type="text">

    <label>Designation</label>
    <input type="text">

    <label>NRIC / Passport No.</label>
    <input type="text">

    <label>Last Day of Service</label>
    <input type="date">


    <!-- ISSUANCE NOTE -->
    <h3>Issuance Note</h3>

    <table id="issueTable">
        <thead>
            <tr>
                <th>No</th>
                <th>Name of Item</th>
                <th>Model / Brand</th>
                <th>Serial Number</th>
                <th>Total Qty</th>
                <th>Issuance Inspection (Personnel)</th>
                <th>Return Inspection (PAA)</th>
                <th>Remarks</th>
            </tr>
        </thead>
        <tbody></tbody>
    </table>

    <button onclick="addIssueRow()">+ Add Item</button>


    <h3>Terms & Conditions</h3>
    <p>
        I verify that I have received all the above listed tools and equipment in its original good condition.
        I understand that if any of the items is found to be lost or damaged, I will be charged at cost of purchase of the items.
        On the other hand, I have to make sure all Company properties are returned in good condition.
    </p>

    <label>Personnel Name</label>
    <input type="text">

    <label>Witness Name</label>
    <input type="text">

    <label>Date</label>
    <input type="date">


    <!-- RETURN NOTE -->
    <h3>Return Note</h3>

    <table id="returnTable">
        <thead>
            <tr>
                <th>No</th>
                <th>Name of Item</th>
                <th>Model / Brand</th>
                <th>Serial Number</th>
                <th>Description of Damage</th>
                <th>Quantity</th>
                <th>Remarks</th>
            </tr>
        </thead>
        <tbody></tbody>
    </table>

    <button onclick="addReturnRow()">+ Add Return Item</button>


    <h3>Return Declaration</h3>

    <label>
        <input type="radio" name="return_statement">
        I have returned all items in its original condition and no cost to be charged.
    </label>

    <label>
        <input type="radio" name="return_statement">
        I have to pay the sum of (MYR):
    </label>
    <input type="text" placeholder="Enter Amount If Applicable">


    <!-- ACKNOWLEDGEMENT -->
    <h3>Acknowledgement</h3>

    <label>Returned By: Name</label>
    <input type="text">

    <label>Designation</label>
    <input type="text">

    <label>Date</label>
    <input type="date">

    <br><br>
    <button onclick="submitForm()">Submit Form</button>


</div>

<div class="container thankyou" id="thankyouMessage">
    <h2>THANK YOU</h2>
    Your submission has been received successfully.
</div>

<script>
    let issueRow = 0;
    let returnRow = 0;

    function addIssueRow(){
        issueRow++;
        const table = document.querySelector("#issueTable tbody");

        const row = document.createElement("tr");
        row.innerHTML = `
            <td>${issueRow}</td>
            <td><input></td>
            <td><input></td>
            <td><input></td>
            <td><input type='number'></td>
            <td>
                <select>
                    <option>OK</option>
                    <option>Defective</option>
                </select>
            </td>
            <td>
                <select>
                    <option>OK</option>
                    <option>Defective</option>
                </select>
            </td>
            <td><input></td>
        `;
        table.appendChild(row);
    }

    function addReturnRow(){
        returnRow++;
        const table = document.querySelector("#returnTable tbody");

        const row = document.createElement("tr");
        row.innerHTML = `
            <td>${returnRow}</td>
            <td><input></td>
            <td><input></td>
            <td><input></td>
            <td><input></td>
            <td><input type='number'></td>
            <td><input></td>
        `;
        table.appendChild(row);
    }

    function submitForm(){
        document.getElementById("formContainer").style.display = "none";
        document.getElementById("thankyouMessage").style.display = "block";
        window.scrollTo(0,0);
    }
</script>

</body>
</html>
