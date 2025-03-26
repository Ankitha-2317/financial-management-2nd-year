# financial-management-2nd-year
c<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Financial Management</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>

    

    <style>
        /* General Styles */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #fbc605;
            text-align: center;
        }

        /* Homepage Styling */
        /* Add an image to the upper part of the homepage */
        .homepage{
            height: 100vh;
            width:100vw;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: url('https://source.unsplash.com/1600x900/?finance,business') no-repeat center center/cover;
            background-size: cover;
            color: rgb(10, 10, 10);
            text-shadow: 2px 2px 10px rgba(246, 243, 243, 0.955);
            position: fixed;
            top: 0;
            left:0;
            padding: 20px;
            text-align: center;
            border: 20px solid black; /* Thick black border on all four sides */
            box-sizing: border-box; /* Ensures the border doesn’t shrink content */
    } 


        /* Title Fix */
        .homepage h1 {
            font-size: 50px;
            text-transform: uppercase;
            opacity: 1;
            position: relative;
            top: -20px; /* Moves title slightly up */
            display: inline-block;
            animation: slideIn 1.2s ease-out 0.5s forwards;
        }
        .homepage p {
            font-size: 20px;
            opacity: 0;
            animation: fadeIn 1.5s ease-in-out 0.5s forwards;
        }
       

        /* Start Button Fix */
        .start-btn {
            background: #0e0e0e;
            color: white;
            padding: 12px 20px;
            font-size: 20px;
            border: none;
            cursor: pointer;
            border-radius: 5px;
            display: block;
            opacity: 1;
            animation: fadeIn 1.5s ease-in-out 0.5s forwards;
            transition: transform 0.3s ease-in-out;
        }

        .start-btn:hover {
            background: #0b0b0b;
            transform: scale(1.1);
        }

        /* Hide Main Content Initially */
        .main-content {
            display: none;
        }

        /* Navigation Bar */
        nav {
            background: #333;
            color: white;
            padding: 15px;
            text-align: center;
            position: fixed;
            width: 100%;
            top: 0;
            left: 0;
            z-index: 1000;
        }

        nav a, .home-btn {
            color: white;
            text-decoration: none;
            margin: 0 15px;
            font-size: 18px;
            cursor: pointer;
            display: inline-block;
            transition: color 0.3s ease-in-out;
        }

        nav a:hover, .home-btn:hover {
            color: #28a745;
        }

        /* Sections */
        section {
            padding: 20px;
            background: white;
            margin: 80px 20px 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: none;
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.5s ease-in-out, transform 0.5s ease-in-out;
        }

        section.active {
            display: block;
            opacity: 1;
            transform: translateY(0);
        }

        /* Formula Section */
        .formula-container {
            width: 80%;
            margin: auto;
            border-collapse: collapse;
        }

        .formula-container th, .formula-container td {
            border: 1px solid black;
            padding: 10px;
            text-align: center;
        }

        .formula-container th {
            background: #fad902;
            color: rgb(14, 14, 14);
        }

        .formula-container td {
            background: #f8f9fa;
            transition: background 0.3s ease-in-out;
        }

        .formula-container td:hover {
            background: #ddd;
        }

        /* Search Input */
        #searchFormula {
            width: 50%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }
        /* Viva Questions Section */
.viva-container {
    width: 80%;
    margin: auto;
    text-align: left;
}

/* Viva Question Buttons */
.viva-question {
    width: 100%;
    padding: 15px;
    font-size: 18px;
    text-align: left;
    background: #f8e406;
    color: rgb(10, 10, 10);
    border: none;
    cursor: pointer;
    margin-top: 5px;
    border-radius: 5px;
    transition: background 0.3s ease-in-out;
}

.viva-question:hover {
    background: #f6e602;
}

/* Viva Answers (Hidden by Default) */
.viva-answer {
    display: none;
    padding: 10px;
    background: #f8f9fa;
    border-left: 3px solid #f9f107;
    margin-bottom: 10px;
    border-radius: 5px;
}
/* Hide all program content initially */
.program-content {
    display: none;
    padding: 20px;
    background: #f8f9fa;
    border: 2px solid #333;
    border-radius: 8px;
    margin-top: 10px;
}

/* Show active program */
.program-content.active {
    display: block;
}

/* Search Bar */
#searchProgram {
    width: 50%;
    padding: 10px;
    margin: 10px 0;
    border: 2px solid #ffd900;
    border-radius: 5px;
    font-size: 16px;
    text-align: center;
}

/* Program Buttons */
.program-buttons button {
    margin: 5px;
    padding: 10px 15px;
    border: none;
    background: #ffea00;
    color: rgb(8, 7, 7);
    cursor: pointer;
    border-radius: 5px;
    transition: 0.3s;
}

.program-buttons button:hover {
    background: #f3d303;
}

/* Styling for Excel Data */
.excel-data {
    margin-top: 10px;
    padding: 10px;
    background: #f8f9fa;
    border: 1px solid #f4cf02;
    border-radius: 5px;
    overflow-x: auto;
    max-height: 300px;
    overflow-y: auto;
}
.experiment {
    margin-bottom: 10px;
}

.experiment-btn {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    background-color: #ffee00;
    color: rgb(15, 15, 15);
    border: none;
    text-align: left;
    cursor: pointer;
}

.experiment-btn:hover {
    background-color: #f6ea05;
}

.experiment-content {
    display: none;
    padding: 10px;
    background-color: #e9ecef;
    border-radius: 5px;
    margin-top: 5px;
}




    </style>
</head>
<body>
    <script>
        function toggleExperiment(expId) {
    let content = document.getElementById("experiment" + expId);
    if (content.style.display === "block") {
        content.style.display = "none";
    } else {
        content.style.display = "block";
    }
}
        function showSection(sectionId) {
    let sections = document.querySelectorAll("section");
    sections.forEach(section => {
        section.style.display = "none";
    });

    document.getElementById(sectionId).style.display = "block";
}

function showAlgorithm(programId) {
    let programs = document.querySelectorAll('.algorithm');
    programs.forEach(program => {
        program.style.display = "none";
    });

    document.getElementById(programId).style.display = "block";
}

        // Include SheetJS
document.write('<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"><\/script>');

// Function to show selected program
function showProgram(programId) {
    let programs = document.querySelectorAll(".program-content");
    programs.forEach(program => program.classList.remove("active"));
    document.getElementById(programId).classList.add("active");
}

// Function to filter programs
function filterPrograms() {
    let input = document.getElementById("searchProgram").value.toLowerCase();
    let buttons = document.querySelectorAll(".program-buttons button");

    buttons.forEach(button => {
        if (button.innerText.toLowerCase().includes(input)) {
            button.style.display = "inline-block";
        } else {
            button.style.display = "none";
        }
    });
}

// Function to read and display Excel data
function readExcel(programNumber) {
    let fileInput = document.getElementById(`excelUpload${programNumber}`);
    let excelDataDiv = document.getElementById(`excelData${programNumber}`);

    if (fileInput.files.length > 0) {
        let file = fileInput.files[0];
        let reader = new FileReader();

        reader.onload = function (e) {
            let data = new Uint8Array(e.target.result);
            let workbook = XLSX.read(data, { type: 'array' });

            let sheet = workbook.Sheets[workbook.SheetNames[0]];
            excelDataDiv.innerHTML = XLSX.utils.sheet_to_html(sheet);
        };

        reader.readAsArrayBuffer(file);
    }
}

        function readExcel(programNumber) {
    let fileInput = document.getElementById(`excelUpload${programNumber}`);
    let excelDataDiv = document.getElementById(`excelData${programNumber}`);

    if (fileInput.files.length > 0) {
        let file = fileInput.files[0];
        let reader = new FileReader();

        reader.onload = function (e) {
            let data = new Uint8Array(e.target.result);
            let workbook = XLSX.read(data, { type: 'array' });

            // Get first sheet
            let sheetName = workbook.SheetNames[0];
            let sheet = workbook.Sheets[sheetName];

            // Convert sheet data to HTML table
            let htmlTable = XLSX.utils.sheet_to_html(sheet);
            excelDataDiv.innerHTML = htmlTable;
        };

        reader.readAsArrayBuffer(file);
    } else {
        excelDataDiv.innerHTML = "❌ No file selected!";
    }
}

        // Function to toggle answers
        function toggleAnswer(questionId) {
            let answer = document.getElementById("answer" + questionId);
            
            if (answer.style.display === "block") {
                answer.style.display = "none";
            } else {
                answer.style.display = "block";
            }
        }
        
        // Function to filter questions
        function filterVivaQuestions() {
            let input = document.getElementById("searchViva").value.toLowerCase();
            let questions = document.querySelectorAll(".viva-item");
        
            questions.forEach(item => {
                let question = item.querySelector(".viva-question").innerText.toLowerCase();
                if (question.includes(input)) {
                    item.style.display = "block";
                } else {
                    item.style.display = "none";
                }
            });
        }

        </script>
        </body>
        </html>
        

    <!-- Homepage -->
    <div class="homepage" id="homepage">
        <h1>FINANCIAL MANAGEMENT <br>(LAB PROGRAMS RESOURCES)</h1>
        <p>WELCOME TO FINANCIAL MANAGEMENT PORTAL</p>
        <button class="start-btn" onclick="startWebsite()">Get Started</button>
    </div>

    <!-- Main Content -->
    <div class="main-content" id="mainContent">
        <!-- Navigation Bar -->
        <nav>
            <span class="home-btn" onclick="goToHome()">🏠 Home</span>
            <a href="javascript:void(0);" onclick="showSection('programs')">Programs</a>
            <a href="javascript:void(0);" onclick="showSection('formulas')">Formulas</a>
            <a href="javascript:void(0);" onclick="showSection('viva-questions')">Viva Questions</a>
           
            
            
        </nav>

        <!-- Formulas Section -->
        <section id="formulas">
            <h2>FINANCIAL FORMULAS</h2>
            <input type="text" id="searchFormula" placeholder="Search formula..." onkeyup="filterFormulas()">
            <table class="formula-container">
                <thead>
                    <tr>
                        <th>FORMULA NAME</th>
                        <th>FORMULA</th>
                        <th>DESCRIPTION</th>
                    </tr>
                </thead>
                <tbody id="formulaList"></tbody>
            </table>
        </section>

    </div>

    <script>
       function startWebsite() {
           

           document.getElementById("homepage").style.display = "none";
           document.getElementById("mainContent").style.display = "block";
           showSection('formulas');
       }


        function goToHome() {
            document.getElementById("mainContent").style.display = "none";
            document.getElementById("homepage").style.display = "flex";
        }

        function showSection(sectionId) {
            let sections = document.querySelectorAll("section");
            sections.forEach(section => section.classList.remove("active"));
            document.getElementById(sectionId).classList.add("active");
        }

        // Financial Formulas List
        const formulas = [
            { name: "Present Value (PV)", formula: "PV = FV / (1 + r)^n", description: "Calculates present value of future cash flow." },
            { name: "Future Value (FV)", formula: "FV = PV * (1 + r)^n", description: "Calculates future value of current investment." },
            { name: "Net Present Value (NPV)", formula: "NPV = Σ [CF / (1 + r)^t]", description: "Determines the profitability of an investment." },
            { name: "Present Value (PV)", formula: " PV = Annuity Amount  x   PVAF(r,n)",description: "PRESENT VALUE OF AN ANNUITY (MULTIPLE AMOUNT) :." },
            { name:  "Present Value (PV)", formula: "PV =   Annual  Cash Flow / r", description: "PRESENT VALUE OF PERPETUITY (INFINITE RETURNS)" },
            { name:  "Future Value (FV)", formula: "FV = PV x CVF(r,n) ", description: "	FUTURE VALUE OF GIVEN AMOUNT (SINGLE AMOUNT)" },
            { name:  "IRR", formula: " IRR=(FV(1/time)/PV)-1", description: "Internal rate of return" },
            { name:  "Future Value ", formula: "A[(1+r) ^n-1/r] ", description: "	Future Value Of Annuity " },
            { name:  "Present value", formula: "FV×1/(1+r) ^n ", description: "	Present Value Of a Single Amount  " },
            { name:  "Present Value  ", formula: "A[1-(1/(1+r) ^n) /r] ", description: "present  Value Of Annuity " },
            { name:  "Future Value ", formula: "[ (1+r) ×P[(1+r) ^n-1/r] ", description: "FV Of Annuity Due " },
            { name:  "Cost Of Debentures ", formula: "(I(1-t)+1/n(RV-NP)) /(0.5+NP) ) *100 ", description: "Cost Of Debentures" },
            

        ];

        function displayFormulas() {
            let formulaList = document.getElementById("formulaList");
            formulaList.innerHTML = "";
            formulas.forEach(f => {
                let row = document.createElement("tr");
                row.innerHTML = `<td>${f.name}</td><td>${f.formula}</td><td>${f.description}</td>`;
                formulaList.appendChild(row);
            });
        }

        function filterFormulas() {
            let input = document.getElementById("searchFormula").value.toLowerCase();
            document.querySelectorAll(".formula-container tbody tr").forEach(row => {
                row.style.display = row.innerText.toLowerCase().includes(input) ? "" : "none";
            });
        }

        window.onload = function() {
            document.getElementById("homepage").style.display = "flex";
            displayFormulas();
        };
    </script>
</body>
</html>
<!-- Viva Questions Section -->
<section id="viva-questions">
    <h2>Viva Questions</h2>

    <!-- Search Bar -->
    <input type="text" id="searchViva" placeholder="Search questions..." onkeyup="filterVivaQuestions()">

    <!-- Viva Questions List -->
    <div class="viva-container">
        <div class="viva-item">
            <button class="viva-question" onclick="toggleAnswer(1)">1. What is Financial Management?</button>
            <div class="viva-answer" id="answer1">
                Financial Management is the process of planning, organizing, directing, and controlling financial resources to achieve an organization's financial goals.
            </div>
        </div>

        <div class="viva-item">
            <button class="viva-question" onclick="toggleAnswer(2)">2. What is Profit? How is it different from Revenue?</button>
            <div class="viva-answer" id="answer2">
                Profit is the financial gain obtained when revenue exceeds expenses. <br>
                <strong>Formula:</strong> Profit = Revenue - Total Expenses
            </div>
        </div>

        <div class="viva-item">
            <button class="viva-question" onclick="toggleAnswer(3)">3. What is Present Value (PV) of Money? Why is it important?</button>
            <div class="viva-answer" id="answer3">
                Present Value (PV) is the current worth of a future sum of money, discounted at a specific rate. <br>
                <strong>Formula:</strong> PV = FV / (1 + r)^n
            </div>
        </div>

        <div class="viva-item">
            <button class="viva-question" onclick="toggleAnswer(4)">4. What is the Future Value (FV) of Money?</button>
            <div class="viva-answer" id="answer4">
                Future Value (FV) is the amount of money an investment will grow to over time with interest. <br>
                <strong>Formula:</strong> FV = PV × (1 + r)^n
            </div>
        </div>

        <div class="viva-item">
            <button class="viva-question" onclick="toggleAnswer(5)">5. What is the Time Value of Money (TVM)?</button>
            <div class="viva-answer" id="answer5">
                The Time Value of Money (TVM) states that money available today is worth more than the same amount in the future due to its earning potential.
            </div>
        </div>

        <div class="viva-item">
            <button class="viva-question" onclick="toggleAnswer(6)">6. What is Cash Flow? How is it different from Profit?</button>
            <div class="viva-answer" id="answer6">
                Cash Flow is the movement of cash in and out of a business, showing liquidity. <br>
                <strong>Types:</strong> Operating Cash Flow, Investing Cash Flow, Financing Cash Flow.
            </div>
        </div>

        <div class="viva-item">
            <button class="viva-question" onclick="toggleAnswer(7)">7. What is Net Present Value (NPV)?</button>
            <div class="viva-answer" id="answer7">
                NPV is the difference between the present value of cash inflows and outflows over a period. <br>
                <strong>Formula:</strong> NPV = Σ [CF / (1 + r)^t] - C0
            </div>
        </div>

        <div class="viva-item">
            <button class="viva-question" onclick="toggleAnswer(8)">8. What is Discounting in Financial Management?</button>
            <div class="viva-answer" id="answer8">
                Discounting is the process of determining the present value of future cash flows by applying a discount rate.
            </div>
        </div>

        <div class="viva-item">
            <button class="viva-question" onclick="toggleAnswer(9)">9. What is the difference between Gross Profit and Net Profit?</button>
            <div class="viva-answer" id="answer9">
                <strong>Gross Profit:</strong> Revenue - Cost of Goods Sold (COGS) <br>
                <strong>Net Profit:</strong> Gross Profit - Operating Expenses - Taxes - Interest
            </div>
        </div>

        <div class="viva-item">
            <button class="viva-question" onclick="toggleAnswer(10)">10. What is a Cash Budget? Why is it important?</button>
            <div class="viva-answer" id="answer10">
                A Cash Budget is a financial plan that estimates cash inflows and outflows over a period. It helps in managing liquidity.
            </div>
        </div>
    </div>
</section>
<!-- Program Section -->
<section id="programs">
    <h2>Programs</h2>

    <!-- Search Bar for Programs -->
    <input type="text" id="searchProgram" placeholder="Search Programs..." onkeyup="filterPrograms()">

    <!-- Program Buttons -->
    <div class="program-buttons">
        <button onclick="showProgram('program1')">Program 1</button>
        <button onclick="showProgram('program2')">Program 2</button>
        <button onclick="showProgram('program3')">Program 3</button>
        <button onclick="showProgram('program4')">Program 4</button>
        <button onclick="showProgram('program5')">Program 5</button>
        <button onclick="showProgram('program6')">Program 6</button>
        <button onclick="showProgram('program7')">Program 7</button>
        <button onclick="showProgram('program8')">Program 8</button>
        <button onclick="showProgram('program9')">Program 9</button>
        <button onclick="showProgram('program10')">Program 10</button>
    </div>

    <!-- Program Sections (Hidden by Default) -->
   <!-- Program 1 -->
<div id="program1" class="program-content">
    <h3>Program 1: Comparing Payment Options</h3>
    
    <p><strong>Problem Statement:</strong></p>
    <p>
        Mr. Raghu sells goods and offers two payment options: <br>
        - Option 1: Pay ₹2500 now <br>
        - Option 2: Pay ₹900 at the end of the 1st, 2nd, and 3rd year <br>
        If the customer's opportunity cost is **10%**, which option should they choose?
    </p>

    <h4>📌 Given Information:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Discount Rate</th>
            <th>Number of Years</th>
            <th>Payment Option</th>
        </tr>
        <tr>
            <td>10% (0.1)</td>
            <td>3</td>
            <td>₹900 per year for 3 years</td>
        </tr>
    </table>

    <h4>📌 Payment Options:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Option</th>
            <th>Payment Details</th>
            <th>Present Value (PV)</th>
        </tr>
        <tr>
            <td>Option 1</td>
            <td>Pay ₹2500 now</td>
            <td>₹2500</td>
        </tr>
        <tr>
            <td>Option 2</td>
            <td>Pay ₹900 at the end of each year for 3 years</td>
            <td>₹2238.17</td>
        </tr>
    </table>

    <h4>📌 Calculation of Present Value for Option 2:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Year</th>
            <th>Amount (₹)</th>
        </tr>
        <tr>
            <td>1</td>
            <td>900</td>
        </tr>
        <tr>
            <td>2</td>
            <td>900</td>
        </tr>
        <tr>
            <td>3</td>
            <td>900</td>
        </tr>
    </table>

    <h4>📌 Calculation Using Excel:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Formula Used</th>
            <th>Result</th>
        </tr>
        <tr>
            <td>PV of annuity formula</td>
            <td>₹2238.17</td>
        </tr>
    </table>

    <h4>📌 Conclusion:</h4>
    <p style="text-align:center;">
        The customer should **select Option 2**, as its present value (₹2238.17) is **less than** the upfront payment of ₹2500 in Option 1. <br>
        Therefore, **Option 2 is the better financial choice.**
    </p>
</div>
<!-- Program 2 -->
<div id="program2" class="program-content">
    <h3>Program 2: Investment Decision on Perpetual Return</h3>
    
    <p><strong>Problem Statement:</strong></p>
    <p>
        A bank offers an investment option where a deposit of ₹16,000 earns a perpetual return of ₹1,800 per year. <br>
        Should an investor accept the offer if their opportunity rate of return is 12%? <br>
        How does the decision change if the rate of return is 10%?
    </p>

    <h4>📌 Given Information:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Initial Investment</th>
            <th>Annual Cash Flow</th>
        </tr>
        <tr>
            <td>₹16,000</td>
            <td>₹1,800</td>
        </tr>
    </table>

    <h4>📌 Case 1: Rate of Return = 12%</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Rate of Return</th>
            <th>Present Value of Perpetuity</th>
            <th>Decision</th>
        </tr>
        <tr>
            <td>12% (0.12)</td>
            <td>₹15,000</td>
            <td style="color:red;"><strong>❌ Reject</strong></td>
        </tr>
    </table>
    <p style="text-align:center;">(PV < Initial Investment, so the offer should be rejected)</p>

    <h4>📌 Case 2: Rate of Return = 10%</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Rate of Return</th>
            <th>Present Value of Perpetuity</th>
            <th>Decision</th>
        </tr>
        <tr>
            <td>10% (0.1)</td>
            <td>₹18,000</td>
            <td style="color:green;"><strong>✅ Accept</strong></td>
        </tr>
    </table>
    <p style="text-align:center;">(PV > Initial Investment, so the offer should be accepted)</p>

    <h4>📌 Conclusion:</h4>
    <p style="text-align:center;">
        The investor should **reject** the offer if their opportunity rate of return is **12%**, <br>
        but **accept** it if their opportunity rate of return is **10%**.
    </p>
</div>
<!-- Program 3 -->
<div id="program3" class="program-content">
    <h3>Program 3: Recurring Deposit & Future Value Calculation</h3>
    
    <p><strong>Problem Statement:</strong></p>
    <p>
        A recurring deposit of ₹100 is made at the **beginning** of each of the next 4 years at an **interest rate of 6% per annum**.  
        Find the **total deposit at the end of** 4 years, 6 years, 10 years, and 15 years.
    </p>

    <h4>📌 Given Information:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Cash Flow (₹ per year)</th>
            <th>Rate of Interest</th>
            <th>Number of Years</th>
        </tr>
        <tr>
            <td>100</td>
            <td>6% (0.06)</td>
            <td>4</td>
        </tr>
    </table>

    <h4>📌 Future Value Calculations:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Duration</th>
            <th>Formula Used</th>
            <th>Future Value (₹)</th>
        </tr>
        <tr>
            <td>4 Years</td>
            <td>Future Value Formula</td>
            <td>463.71</td>
        </tr>
        <tr>
            <td>6 Years</td>
            <td>Using Excel</td>
            <td>739.38</td>
        </tr>
        <tr>
            <td>10 Years</td>
            <td>Using Excel</td>
            <td>1,397.16</td>
        </tr>
        <tr>
            <td>15 Years</td>
            <td>Using Excel</td>
            <td>2,467.25</td>
        </tr>
    </table>

    <h4>📌 Conclusion:</h4>
    <p style="text-align:center;">
        The **future value of the recurring deposit increases** significantly over time due to **compound interest**.  
        Investing for a **longer duration results in higher returns**.
    </p>
</div>
<!-- Program 4 -->
<div id="program4" class="program-content">
    <h3>Program 4: Sinking Fund Annual Contribution Calculation</h3>

    <p><strong>Problem Statement:</strong></p>
    <p>
        A company is establishing a sinking fund to retire ₹500,000, 8% debentures, 10 years from today.  
        The company will contribute a fixed amount annually for 10 years, earning 6% per year.  
        Calculate the equal annual contributions needed to accumulate ₹500,000.
    </p>

    <h4>📌 Given Information:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Target Amount</th>
            <th>Interest Rate</th>
            <th>Number of Years</th>
        </tr>
        <tr>
            <td>₹500,000</td>
            <td>8% (0.08)</td>
            <td>10</td>
        </tr>
    </table>

    <h4>📌 Compounded Value Factor of an Annuity:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Earning Rate</th>
            <th>CVFA for 6% (10 Years)</th>
        </tr>
        <tr>
            <td>6% (0.06)</td>
            <td>13.181</td>
        </tr>
    </table>

    <h4>📌 Annual Contributions Required:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Method</th>
            <th>Annual Contribution</th>
        </tr>
        <tr>
            <td>Formula Calculation</td>
            <td>₹37,933.98</td>
        </tr>
        <tr>
            <td>Using CVFA Table</td>
            <td>₹37,933.39</td>
        </tr>
        <tr>
            <td>Using Excel Formula</td>
            <td>₹-37,933.98</td>
        </tr>
    </table>

    <h4>📌 Conclusion:</h4>
    <p style="text-align:center;">
        The company must make an annual contribution of approximately ₹37,933.39  
        to accumulate ₹500,000 in 10 years at an earning rate of 6%.
    </p>
</div>
<!-- Program 5 -->
<div id="program5" class="program-content">
    <h3>Program 5: Net Present Value (NPV) Calculation</h3>

    <p><strong>Problem Statement:</strong></p>
    <p>
        A machine is available for ₹1,70,000 and has a life of 5 years.  
        It is expected to generate cash flows of ₹20,000, ₹50,000, ₹60,000, ₹40,000, and ₹75,000.  
        Find out the NPV of the machine given the required rate of return as 10%.
    </p>

    <h4>📌 Given Information:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Initial Investment</th>
            <th>Rate of Return</th>
        </tr>
        <tr>
            <td>₹1,70,000</td>
            <td>10% (0.1)</td>
        </tr>
    </table>

    <h4>📌 Cash Flow Details:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Year</th>
            <th>Cash Flow (₹)</th>
        </tr>
        <tr><td>1</td><td>20,000</td></tr>
        <tr><td>2</td><td>50,000</td></tr>
        <tr><td>3</td><td>60,000</td></tr>
        <tr><td>4</td><td>40,000</td></tr>
        <tr><td>5</td><td>75,000</td></tr>
    </table>

    <h4>📌 NPV Calculation Using Formula:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Year</th>
            <th>Cash Flow (₹)</th>
            <th>Discount Factor</th>
            <th>Discounted Cash Flow (₹)</th>
        </tr>
        <tr><td>0</td><td>-1,70,000</td><td>-</td><td>-</td></tr>
        <tr><td>1</td><td>20,000</td><td>1.100</td><td>18,182</td></tr>
        <tr><td>2</td><td>50,000</td><td>1.210</td><td>41,322</td></tr>
        <tr><td>3</td><td>60,000</td><td>1.331</td><td>45,079</td></tr>
        <tr><td>4</td><td>40,000</td><td>1.464</td><td>27,321</td></tr>
        <tr><td>5</td><td>75,000</td><td>1.611</td><td>46,569</td></tr>
        <tr>
            <th colspan="3">Total Present Value of Cash Flows</th>
            <th>₹1,78,473</th>
        </tr>
    </table>

    <h4>📌 NPV Calculation:</h4>
    <p>
        <strong>NPV = Total Present Value of Cash Flows - Initial Investment</strong>  
        <strong>NPV = ₹1,78,473 - ₹1,70,000 = ₹8,473</strong>
    </p>

    <h4>📌 NPV Using Excel Formula:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Excel Formula Used</th>
            <th>NPV (₹)</th>
        </tr>
        <tr>
            <td>=NPV(10%, cash flows) - Initial Investment</td>
            <td>₹8,473</td>
        </tr>
    </table>

    <h4>📌 Conclusion:</h4>
    <p style="text-align:center;">
        Since the NPV is positive (₹8,473), the project is **financially viable** and should be accepted.
    </p>
</div>
<!-- Program 6 -->
<div id="program6" class="program-content">
    <h3>Program 6: Internal Rate of Return (IRR) Calculation</h3>

    <p><strong>Problem Statement:</strong></p>
    <p>
        A firm is evaluating a proposal costing ₹1,60,000, expected to generate cash flows of ₹40,000, ₹60,000, ₹50,000, ₹50,000, and ₹40,000.  
        There is no salvage value. Find out the IRR of the proposal. Also, determine whether the proposal is suitable for acceptance  
        if the hurdle rate of the firm is 12%.
    </p>

    <h4>📌 Given Information:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Cost of the Proposal</th>
            <th>Hurdle Rate</th>
        </tr>
        <tr>
            <td>₹1,60,000</td>
            <td>12% (0.12)</td>
        </tr>
    </table>

    <h4>📌 Cash Flow Details:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Year</th>
            <th>Cash Flow (₹)</th>
        </tr>
        <tr><td>0</td><td>-1,60,000</td></tr>
        <tr><td>1</td><td>40,000</td></tr>
        <tr><td>2</td><td>60,000</td></tr>
        <tr><td>3</td><td>50,000</td></tr>
        <tr><td>4</td><td>50,000</td></tr>
        <tr><td>5</td><td>40,000</td></tr>
    </table>

    <h4>📌 IRR Calculation Using Formula:</h4>

    <h4>Step 1: Fake Payback Period</h4>
    <p>
        <strong>Fake Payback Period = Initial Investment / Average Cash Inflow</strong><br>
        Average Cash Inflow = (40,000 + 60,000 + 50,000 + 50,000 + 40,000) / 5 = ₹48,000<br>
        <strong>Fake Payback Period = ₹1,60,000 / ₹48,000 = 3.33 years</strong>
    </p>

    <h4>Step 2: Checking the PVIF Table</h4>
    <p>
        Based on the PVIF table, the discount rate that closely matches the payback period lies between **15% and 16%**.
    </p>

    <h4>Step 3: Present Value Calculation</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Year</th>
            <th>Cash Flow (₹)</th>
            <th>PV Factor @ 15%</th>
            <th>PV @ 15% (₹)</th>
            <th>PV Factor @ 16%</th>
            <th>PV @ 16% (₹)</th>
        </tr>
        <tr><td>1</td><td>40,000</td><td>0.87</td><td>34,800</td><td>0.862</td><td>34,480</td></tr>
        <tr><td>2</td><td>60,000</td><td>0.756</td><td>45,360</td><td>0.743</td><td>44,580</td></tr>
        <tr><td>3</td><td>50,000</td><td>0.658</td><td>32,900</td><td>0.641</td><td>32,050</td></tr>
        <tr><td>4</td><td>50,000</td><td>0.572</td><td>28,600</td><td>0.552</td><td>27,600</td></tr>
        <tr><td>5</td><td>40,000</td><td>0.497</td><td>19,880</td><td>0.476</td><td>19,040</td></tr>
        <tr>
            <th colspan="3">Total Present Value</th>
            <th>₹1,61,540</th>
            <th></th>
            <th>₹1,57,750</th>
        </tr>
    </table>

    <h4>Step 4: IRR Calculation</h4>
    <p>
        <strong>IRR Formula:</strong>  
        [
        IRR = lower rate +{[(PV @lower rate -cash outflow)/(pv@lower rate -pv @higher rate)]*difference in rate}

        ]
        <br>
        [
        IRR = 15% + ( {1,61,540 - 1,60,000}{1,61,540 - 1,57,750} ) (16\% - 15\%)
        ]
        <br>
        [
        IRR = 15% + ( {1,540}{3,790} )  1%
        ]
        <br>
        [
        IRR = 15% + 0.406* 1%
        ]
        <br>
        [
        IRR = 15.40\%
        ]
    </p>

    <h4>📌 IRR Using Excel Formula:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Excel Formula Used</th>
            <th>IRR (%)</th>
        </tr>
        <tr>
            <td>=IRR(cash flows)</td>
            <td>15.40%</td>
        </tr>
    </table>

    <h4>📌 Conclusion:</h4>
    <p style="text-align:center;">
        Since **IRR (15.40%) is greater than the hurdle rate (12%)**, the project is **financially viable** and should be accepted.
    </p>
</div>
<!-- Program 7 -->
<div id="program7" class="program-content">
    <h3>Program 7: Payback Period Calculation for ITC Ltd.</h3>

    <p><strong>Problem Statement:</strong></p>
    <p>
        ITC Ltd. is evaluating three different machines to expand production capacity. The company aims to determine  
        the most profitable investment using the <strong>Payback Method</strong>. The details for the three machines, including  
        sales, costs, tax rate, and scrap value, are provided below.
    </p>

    <h4>📌 Given Information:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Particulars</th>
            <th>Machine 1</th>
            <th>Machine 2</th>
            <th>Machine 3</th>
        </tr>
        <tr>
            <td><strong>Initial Investment (₹)</strong></td>
            <td>3,00,000</td>
            <td>3,00,000</td>
            <td>3,00,000</td>
        </tr>
        <tr>
            <td>Estimated Annual Sales (₹)</td>
            <td>5,00,000</td>
            <td>4,00,000</td>
            <td>4,50,000</td>
        </tr>
        <tr>
            <td>Scrap Value (₹)</td>
            <td>40,000</td>
            <td>25,000</td>
            <td>30,000</td>
        </tr>
        <tr>
            <td>Economic Life (Years)</td>
            <td>2</td>
            <td>3</td>
            <td>3</td>
        </tr>
    </table>

    <h4>📌 Estimated Cost of Production:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Cost Component</th>
            <th>Machine 1 (₹)</th>
            <th>Machine 2 (₹)</th>
            <th>Machine 3 (₹)</th>
        </tr>
        <tr><td>Direct Materials</td><td>40,000</td><td>50,000</td><td>48,000</td></tr>
        <tr><td>Direct Labour</td><td>50,000</td><td>30,000</td><td>36,000</td></tr>
        <tr><td>Factory Overheads</td><td>60,000</td><td>50,000</td><td>58,000</td></tr>
        <tr><td>Administration Costs</td><td>20,000</td><td>10,000</td><td>15,000</td></tr>
        <tr><td>Selling & Distribution Costs</td><td>10,000</td><td>10,000</td><td>10,000</td></tr>
    </table>

    <h4>📌 Payback Period Calculation:</h4>

    <h4>Step 1: Depreciation Calculation</h4>
    <p>
        [
          {Depreciation} = {\text{Initial Investment} - {Scrap Value}}{{Economic Life}}
        ]
    </p>

    <table border="1" cellpadding="5">
        <tr>
            <th>Machine</th>
            <th>Depreciation (₹)</th>
        </tr>
        <tr><td>Machine 1</td><td>₹1,30,000</td></tr>
        <tr><td>Machine 2</td><td>₹91,667</td></tr>
        <tr><td>Machine 3</td><td>₹90,000</td></tr>
    </table>

    <h4>Step 2: Cash Flow Before Taxes</h4>
    <p>
        [
          {Cash Flow Before Taxes} = {Annual Sales} - {Total Cost of Production}
        ]
    </p>

    <table border="1" cellpadding="5">
        <tr>
            <th>Machine</th>
            <th>Total Cost of Production (₹)</th>
            <th>Cash Flow Before Taxes (₹)</th>
        </tr>
        <tr><td>Machine 1</td><td>3,10,000</td><td>₹1,90,000</td></tr>
        <tr><td>Machine 2</td><td>2,41,667</td><td>₹1,58,333</td></tr>
        <tr><td>Machine 3</td><td>2,57,000</td><td>₹1,93,000</td></tr>
    </table>

    <h4>Step 3: Tax Calculation</h4>
    <p>
        [
         {Taxes} = {Cash Flow Before Taxes}30%
        ]
    </p>

    <table border="1" cellpadding="5">
        <tr>
            <th>Machine</th>
            <th>Taxes (₹)</th>
        </tr>
        <tr><td>Machine 1</td><td>₹57,000</td></tr>
        <tr><td>Machine 2</td><td>₹47,500</td></tr>
        <tr><td>Machine 3</td><td>₹57,900</td></tr>
    </table>

    <h4>Step 4: Cash Flow After Taxes</h4>
    <p>
        [
          {Cash Flow After Taxes} = {Cash Flow Before Taxes} - {Taxes}
        ]
    </p>

    <table border="1" cellpadding="5">
        <tr>
            <th>Machine</th>
            <th>Cash Flow After Taxes (₹)</th>
        </tr>
        <tr><td>Machine 1</td><td>₹2,63,000</td></tr>
        <tr><td>Machine 2</td><td>₹2,02,500</td></tr>
        <tr><td>Machine 3</td><td>₹2,25,100</td></tr>
    </table>

    <h4>Step 5: Payback Period Calculation</h4>
    <p>
        [
           {Payback Period} = {{Initial Investment}}{{Cash Flow After Taxes}}
        ]
    </p>

    <table border="1" cellpadding="5">
        <tr>
            <th>Machine</th>
            <th>Payback Period (Years)</th>
        </tr>
        <tr><td>Machine 1</td><td>1.14</td></tr>
        <tr><td>Machine 2</td><td>1.48</td></tr>
        <tr><td>Machine 3</td><td>1.33</td></tr>
    </table>

    <h4>📌 Conclusion:</h4>
    <p style="text-align:center;">
        Since Machine 1 has the **shortest payback period (1.14 years)**, it is the **most profitable investment** based on the **Payback Method**.
    </p>
</div>
<!-- Program 8 -->
<div id="program8" class="program-content">
    <h3>Program 8: Investment Proposal Analysis for Milling Controls</h3>

    <p><strong>Problem Statement:</strong></p>
    <p>
        A company is evaluating an investment proposal to install new milling controls at a cost of ₹50,000.  
        The facility has a **5-year life expectancy** with **no salvage value**. The **tax rate is 35%**,  
        and the company uses **straight-line depreciation** for tax purposes.  
    </p>
    <p><strong>Required calculations:</strong></p>
    <ul>
        <li>(i) Payback Period (PBP)</li>
        <li>(ii) Average Rate of Return (ARR)</li>
        <li>(iii) Internal Rate of Return (IRR)</li>
        <li>(iv) Net Present Value (NPV) at a 10% discount rate</li>
        <li>(v) Profitability Index (PI) at a 10% discount rate</li>
    </ul>

    <h4>📌 Given Information:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Particulars</th>
            <th>Values</th>
        </tr>
        <tr>
            <td>Initial Investment (₹)</td>
            <td>50,000</td>
        </tr>
        <tr>
            <td>Project Life (Years)</td>
            <td>5</td>
        </tr>
        <tr>
            <td>Salvage Value (₹)</td>
            <td>0</td>
        </tr>
        <tr>
            <td>Tax Rate</td>
            <td>35%</td>
        </tr>
        <tr>
            <td>Discount Rate</td>
            <td>10%</td>
        </tr>
    </table>

    <h4>📌 Estimated Cash Flows (CFBT):</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Year</th>
            <th>Cash Flow Before Tax (CFBT) (₹)</th>
        </tr>
        <tr><td>1</td><td>10,000</td></tr>
        <tr><td>2</td><td>10,692</td></tr>
        <tr><td>3</td><td>12,769</td></tr>
        <tr><td>4</td><td>13,462</td></tr>
        <tr><td>5</td><td>20,385</td></tr>
    </table>

    <h4>📌 Step 1: Depreciation Calculation</h4>
    <p>
        Since the company uses **straight-line depreciation**, we calculate it as:
        [
        {Depreciation} = {{Initial Investment} - {Salvage Value}}{{Life of Asset}}
        ]
        [
        = {50,000 - 0}{5} = ₹10,000{ per year}
        ]
    </p>

    <h4>📌 Step 2: Tax and Cash Flow After Tax (CFAT)</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Year</th>
            <th>CBFT (₹)</th>
            <th>Depreciation (₹)</th>
            <th>CFBTAD (₹)</th>
            <th>Tax @ 35% (₹)</th>
            <th>CFAT (₹)</th>
        </tr>
        <tr><td>1</td><td>10,000</td><td>10,000</td><td>0</td><td>0</td><td>10,000</td></tr>
        <tr><td>2</td><td>10,692</td><td>10,000</td><td>692</td><td>242</td><td>10,450</td></tr>
        <tr><td>3</td><td>12,769</td><td>10,000</td><td>2,769</td><td>969</td><td>11,800</td></tr>
        <tr><td>4</td><td>13,462</td><td>10,000</td><td>3,462</td><td>1,212</td><td>12,250</td></tr>
        <tr><td>5</td><td>20,385</td><td>10,000</td><td>10,385</td><td>3,635</td><td>16,750</td></tr>
    </table>

    <h4>📌 Step 3: Payback Period (PBP)</h4>
    <p>
        [
         {PBP} = {{Initial Investment}}{{Cumulative CFAT}}
        ]
        [
        = 4.33{ years}
        ]
    </p>

    <h4>📌 Step 4: Average Rate of Return (ARR)</h4>
    <p>
        [
          {ARR} = {{Average Annual Profit After Tax}}{{Initial Investment}} 100
        ]
        [
        = 24.50\%
        ]
    </p>

    <h4>📌 Step 5: Internal Rate of Return (IRR)</h4>
    <p>
        Using trial and error, IRR is calculated as:
        [
          {IRR} = 6.58\%
        ]
    </p>

    <h4>📌 Step 6: Net Present Value (NPV) at 10% Discount Rate</h4>
    <p>
        [
           {NPV} = sum{{CFAT}}{(1+0.10)^t} - {Initial Investment}
        ]
        [
        = ₹-4,217.98
        ]
    </p>

    <h4>📌 Step 7: Profitability Index (PI) at 10% Discount Rate</h4>
    <p>
        [
          {PI} = {{Present Value of Future Cash Flows}}{{Initial Investment}}
        ]
       [
        = ₹0.91
        ]
    </p>

    <h4>📌 Conclusion:</h4>
    <p style="text-align:center;">
        Since the **NPV is negative (-₹4,217.98)**, **IRR is lower than 10%**, and **PI is below 1.0**,  
        the investment is **not financially viable** and should be rejected.
    </p>
</div>
<!-- Program 9 -->
<div id="program9" class="program-content">
    <h3>Program 9: Calculation of Explicit Cost of Debt</h3>

    <p><strong>Problem Statement:</strong></p>
    <p>
        Calculate the **explicit cost of debt** under the following three cases:  
        <ul>
            <li>(a) Debentures sold at par with flotation costs of 5%.</li>
            <li>(b) Debentures sold at a **premium of 10%** with flotation costs of 5%.</li>
            <li>(c) Debentures sold at a **discount of 5%** with flotation costs of 5%.</li>
        </ul>
    </p>

    <h4>📌 Given Information:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Particulars</th>
            <th>Values</th>
        </tr>
        <tr>
            <td>Coupon Rate of Interest</td>
            <td>10%</td>
        </tr>
        <tr>
            <td>Face Value of Debenture (₹)</td>
            <td>100</td>
        </tr>
        <tr>
            <td>Maturity Period (Years)</td>
            <td>10</td>
        </tr>
        <tr>
            <td>Tax Rate</td>
            <td>35%</td>
        </tr>
        <tr>
            <td>Flotation Cost</td>
            <td>5%</td>
        </tr>
    </table>

    <h4>📌 Formula for Cost of Debt:</h4>
    <p>
        \[
        k_d = \frac{I(1 - t) + \frac{1}{n} (RV - NP)}{\frac{1}{2} (RV + NP)} \times 100
        \]
        <ul>
            <li>\( I \) = Annual interest payment (₹10 per ₹100 face value)</li>
            <li>\( t \) = Tax rate (35%)</li>
            <li>\( RV \) = Redeemable value (Varies for each case)</li>
            <li>\( NP \) = Net proceeds after flotation cost (Varies for each case)</li>
            <li>\( n \) = Maturity period (10 years)</li>
        </ul>
    </p>

    <h4>📌 Step 1: Cost of Debentures Calculation</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Particulars</th>
            <th>Debentures Sold at Par</th>
            <th>Debentures Sold at Premium</th>
            <th>Debentures Sold at Discount</th>
        </tr>
        <tr>
            <td>Interest (₹)</td>
            <td>10.00</td>
            <td>10.00</td>
            <td>10.00</td>
        </tr>
        <tr>
            <td>Face Value (₹)</td>
            <td>100</td>
            <td>100</td>
            <td>100</td>
        </tr>
        <tr>
            <td>Premium / Discount</td>
            <td>—</td>
            <td>10% Premium</td>
            <td>5% Discount</td>
        </tr>
        <tr>
            <td>Flotation Cost</td>
            <td>5%</td>
            <td>5%</td>
            <td>5%</td>
        </tr>
        <tr>
            <td>Redeemable Value (₹)</td>
            <td>100</td>
            <td>110</td>
            <td>95</td>
        </tr>
        <tr>
            <td>Net Proceeds (₹)</td>
            <td>95</td>
            <td>95</td>
            <td>95</td>
        </tr>
        <tr>
            <td>Tax-adjusted Interest</td>
            <td>\(10 \times (1 - 0.35) = 6.5\)</td>
            <td>\(10 \times (1 - 0.35) = 6.5\)</td>
            <td>\(10 \times (1 - 0.35) = 6.5\)</td>
        </tr>
        <tr>
            <td>Cost of Debt (\( k_d \))</td>
            <td><strong>7.18%</strong></td>
            <td><strong>7.80%</strong></td>
            <td><strong>6.84%</strong></td>
        </tr>
    </table>

    <h4>📌 Conclusion:</h4>
    <ul>
        <li>The **highest cost of debt** is when **debentures are sold at a premium (7.80%)**.</li>
        <li>The **lowest cost of debt** is when **debentures are sold at a discount (6.84%)**.</li>
        <li>For **debentures sold at par**, the cost of debt is **7.18%**.</li>
    </ul>
</div>
<!-- Program 9 -->
<div id="program9" class="program-content">
    <h3>Program 9: Calculation of Explicit Cost of Debt</h3>

    <p><strong>Problem Statement:</strong></p>
    <p>
        Calculate the **explicit cost of debt** under the following three cases:  
        <ul>
            <li>(a) Debentures sold at par with flotation costs of 5%.</li>
            <li>(b) Debentures sold at a **premium of 10%** with flotation costs of 5%.</li>
            <li>(c) Debentures sold at a **discount of 5%** with flotation costs of 5%.</li>
        </ul>
    </p>

    <h4>📌 Given Information:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Particulars</th>
            <th>Values</th>
        </tr>
        <tr>
            <td>Coupon Rate of Interest</td>
            <td>10%</td>
        </tr>
        <tr>
            <td>Face Value of Debenture (₹)</td>
            <td>100</td>
        </tr>
        <tr>
            <td>Maturity Period (Years)</td>
            <td>10</td>
        </tr>
        <tr>
            <td>Tax Rate</td>
            <td>35%</td>
        </tr>
        <tr>
            <td>Flotation Cost</td>
            <td>5%</td>
        </tr>
    </table>

    <h4>📌 Formula for Cost of Debt:</h4>
    <p>
        [
        k_d = frac{I(1 - t) + frac{1}{n} (RV - NP)}{frac{1}{2} (RV + NP)} times 100
        ]
        <ul>
            <li>( I ) = Annual interest payment (₹10 per ₹100 face value)</li>
            <li>( t ) = Tax rate (35%)</li>
            <li>( RV ) = Redeemable value (Varies for each case)</li>
            <li>( NP ) = Net proceeds after flotation cost (Varies for each case)</li>
            <li>( n ) = Maturity period (10 years)</li>
        </ul>
    </p>

    <h4>📌 Step 1: Cost of Debentures Calculation</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Particulars</th>
            <th>Debentures Sold at Par</th>
            <th>Debentures Sold at Premium</th>
            <th>Debentures Sold at Discount</th>
        </tr>
        <tr>
            <td>Interest (₹)</td>
            <td>10.00</td>
            <td>10.00</td>
            <td>10.00</td>
        </tr>
        <tr>
            <td>Face Value (₹)</td>
            <td>100</td>
            <td>100</td>
            <td>100</td>
        </tr>
        <tr>
            <td>Premium / Discount</td>
            <td>—</td>
            <td>10% Premium</td>
            <td>5% Discount</td>
        </tr>
        <tr>
            <td>Flotation Cost</td>
            <td>5%</td>
            <td>5%</td>
            <td>5%</td>
        </tr>
        <tr>
            <td>Redeemable Value (₹)</td>
            <td>100</td>
            <td>110</td>
            <td>95</td>
        </tr>
        <tr>
            <td>Net Proceeds (₹)</td>
            <td>95</td>
            <td>95</td>
            <td>95</td>
        </tr>
        <tr>
            <td>Tax-adjusted Interest</td>
            <td>\(10 \times (1 - 0.35) = 6.5\)</td>
            <td>\(10 \times (1 - 0.35) = 6.5\)</td>
            <td>\(10 \times (1 - 0.35) = 6.5\)</td>
        </tr>
        <tr>
            <td>Cost of Debt (\( k_d \))</td>
            <td><strong>7.18%</strong></td>
            <td><strong>7.80%</strong></td>
            <td><strong>6.84%</strong></td>
        </tr>
    </table>

    <h4>📌 Conclusion:</h4>
    <ul>
        <li>The **highest cost of debt** is when **debentures are sold at a premium (7.80%)**.</li>
        <li>The **lowest cost of debt** is when **debentures are sold at a discount (6.84%)**.</li>
        <li>For **debentures sold at par**, the cost of debt is **7.18%**.</li>
    </ul>
</div>
<!-- Program 10 -->
<div id="program10" class="program-content">
    <h3>Program 10: Calculation of Weighted Average Cost of Capital (WACC)</h3>

    <p><strong>Problem Statement:</strong></p>
    <p>
        Calculate the **Weighted Average Cost of Capital (WACC)** for Avinash Metals using the following details:  
        <ul>
            <li>Net Operating Income (NOI): ₹40 million</li>
            <li>Interest on Debt: ₹10 million</li>
            <li>Cost of Equity: 18%</li>
            <li>Cost of Debt: 12%</li>
        </ul>
        Also, analyze the impact on WACC if the company raises **₹100 million of additional debt** to finance a new project that generates an additional **₹20 million of NOI** (Assume NOI method and no tax).
    </p>

    <h4>📌 Given Information:</h4>
    <table border="1" cellpadding="5">
        <tr>
            <th>Particulars</th>
            <th>Amount</th>
        </tr>
        <tr>
            <td>Net Operating Income (NOI)</td>
            <td>₹40 million</td>
        </tr>
        <tr>
            <td>Interest on Debt</td>
            <td>₹10 million</td>
        </tr>
        <tr>
            <td>Cost of Equity</td>
            <td>18%</td>
        </tr>
        <tr>
            <td>Cost of Debt</td>
            <td>12%</td>
        </tr>
    </table>

    <h4>📌 Step 1: Compute Amount of Debt & Equity</h4>
    <p>Using the Net Operating Income (NOI) method:</p>
    <ul>
        <li>Net Income = NOI - Interest = ₹40 million - ₹10 million = ₹30 million</li>
        <li>Equity Capital = Net Income / Cost of Equity  
            \[
               {Equity} = \frac{30,000,000}{0.18} = ₹166.67{ million}
            \]
        </li>
        <li>Debt is already given as ₹83.33 million.</li>
    </ul>

    <h4>📌 Step 2: Compute Weighted Average Cost of Capital (WACC)</h4>
    <p>The WACC formula is:</p>
    <p>
        [
        WACC =( \frac{E}{V} \times k_e ) + ( \frac{D}{V} \times k_d)
        ]
        where:
        <ul>
            <li>( E ) = Equity (₹166.67 million)</li>
            <li>( D ) = Debt (₹83.33 million)</li>
            <li>( V ) = Total Capital = E + D = ₹250 million</li>
            <li>( k_e ) = Cost of Equity (18%)</li>
            <li>( k_d ) = Cost of Debt (12%)</li>
        </ul>
    </p>

    <h4>📌 Step 3: WACC Calculation</h4>
    <p>
        [
        WACC = ( \frac{166.67}{250} \times 0.18 ) + ( frac{83.33}{250} times 0.12)
        ]
        [
        WACC = (0.6667 \ 0.18) + (0.3333 \ 0.12)
        ]
        [
        WACC = 0.12 + 0.04 = 0.16 = 16%
        ]
    </p>

    <h3>📌 Part (b): Impact of Additional ₹100 Million Debt</h3>
    <p>New project details:</p>
    <ul>
        <li>Additional Debt = ₹100 million</li>
        <li>New Net Operating Income (NOI) = ₹40 million + ₹20 million = ₹60 million</li>
        <li>New Interest on Debt = ₹10 million + (12% of ₹100 million) = ₹22 million</li>
        <li>New Net Income = ₹60 million - ₹22 million = ₹38 million</li>
        <li>New Equity = ₹38 million / 18% = ₹211.11 million</li>
        <li>New Total Capital = ₹211.11 million (Equity) + ₹183.33 million (Debt) = ₹394.44 million</li>
    </ul>

    <h4>📌 Step 2: New WACC Calculation</h4>
    <p>
        [
        WACC = ( frac{211.11}{394.44} * 0.18 ) + ( frac{183.33}{394.44} * 0.12)
        ]
        [
        WACC = (0.5356* 0.18) + (0.4644 * 0.12)
        ]
        [
        WACC = 0.0964 + 0.0557 = 0.1521 = 15.21\%
        ]
    </p>

    <h4>📌 Conclusion:</h4>
    <ul>
        <li>Initial WACC = **16%**</li>
        <li>After raising additional **₹100 million** of debt, the new WACC **decreases to 15.21%**.</li>
        <li>Since debt is cheaper than equity, adding more debt reduces WACC.</li>
    </ul>
</div>
<!-- Steps Section -->
<div id="steps" class="content-section">
    <h2>Steps</h2>

    <div class="experiment-container">
        <!-- Experiments 1 to 10 -->
        <div class="experiment">
            <button class="experiment-btn" onclick="toggleExperiment(1)">Experiment 1</button>
            <div class="experiment-content" id="experiment1">
                <p><strong>Step 1:</strong> Open MS Excel and create a new spreadsheet</p>
                <p><strong>Step 2:</strong> Note down given information in cells</p>
                <p><strong>Step 3:</strong> Applying relevant formulas</p>
                <p>Method 1: By mathematical formula: PV = PMT * (1 - (1 / (1 + r)^n) / r)</p>
                <p>Method 2: By financial formula: =PV(nper,rate,pmt,,type)</p>
                <p>Method 3: Using formula tool: Go to View → Formulas → Financial → PV</p>
            </div>
        </div>

        <div class="experiment">
            <button class="experiment-btn" onclick="toggleExperiment(2)">Experiment 2</button>
            <div class="experiment-content" id="experiment2">
                <p><strong>Step 1:</strong> Open MS Excel and create a new spreadsheet</p>
                <p><strong>Step 2:</strong> Note down given information in cells</p>
                <p><strong>Step 3:</strong> Apply formulas to solve the statement</p>
                <p>Method 1: By mathematical formula: PV = Pmt / i</p>
                <p>Method 2: By financial formula: =PV(nper,rate,pmt,,type)</p>
                <p>Method 3: Using formula tool: Go to View → Formulas → Financial → PV</p>
            </div>
        </div>

        <div class="experiment">
            <button class="experiment-btn" onclick="toggleExperiment(3)">Experiment 3</button>
            <div class="experiment-content" id="experiment3">
                <p><strong>Step 1:</strong> Open MS Excel and create a new spreadsheet</p>
                <p><strong>Step 2:</strong> Note down given information in cells</p>
                <p><strong>Step 3:</strong> Calculate below using:</p>
                <p>Method 1: By financial formula: =FV(nper,rate,pmt,,type)</p>
                <p>Method 2: Using formula tool: Go to View → Formulas → Financial → FV</p>
            </div>
        </div>
        <div class="experiment">
            <button class="experiment-btn" onclick="toggleExperiment(4)">Experiment 4</button>
            <div class="experiment-content" id="experiment4">
                <p><strong>Step 1:</strong> Open MS Excel and create a new spreadsheet</p>
                <p><strong>Step 2:</strong> Note down given information in cells</p>
                <p><strong>Step 3:</strong> Calculate below using:</p>
                <p>Method 1: Attach a link of time value of money table stored in Google drive. 
                    Take the value from table and Calculate it below</p>
                <p>Method 2: By using financial formula: 
                    =PMT(nper,rate,pmt,,type) 
                    Select the cells containing above data 
                    Click on enter </p>
                    <p>Method 3: By using formula tool 
                        Go to view->Formulas->Financial ->PMT 
                        There a dialogue box appears and select the cells  containing respective data 
                        Click ok after entering all the details </p>

            </div>
        </div>
        <div class="experiment">
            <button class="experiment-btn" onclick="toggleExperiment(5)">Experiment 5</button>
            <div class="experiment-content" id="experiment5">
                <p><strong>Step 1:</strong> Open MS Excel and create a new spreadsheet</p>
                <p><strong>Step 2:</strong> Note down given information in cells</p>
                <p><strong>Step 3:</strong> Calculate below using:</p>
                <p>Method 1:  Mathematical formulas: 
                    Calculate NPV By sum of all PV. 
                    Where P:Principle amount 
                    </p>
                <p>Method 2: By using financial formula: 
                    =NPV(nper,rate,pmt,,type) 
                    Select the cells containing above data 
                    Click on enter </p>
                    <p>Method 3: :By using formula tool 
                        Go to view->Formulas->Financial ->NPV 
                        There a dialogue box appears and select the cells  containing respective data 
                        Click ok after entering all the details </p>

            </div>
        </div>
        <div class="experiment">
            <button class="experiment-btn" onclick="toggleExperiment(6)">Experiment 6</button>
            <div class="experiment-content" id="experiment6">
                <p><strong>Step 1:</strong> Open MS Excel and create a new spreadsheet</p>
                <p><strong>Step 2:</strong> Note down given information in cells</p>
                <p><strong>Step 3:</strong> Calculate below using:</p>
                <p>Method 1:Calculate below using: 
                    Method 1: Mathematical formulas: 
                    IRR=lr+{[(PV@lr-cashflow)/(pv@lr-pv@hr)]*difference in rate} 
                    Where lr:lower rate 
                    Hr:higher rate </p>
                <p>Method 2: By using financial difference: 
                    =IRR(nper,rate,pmt,,type) 
                    Select the cells containing above data 
                    Click on enter </p>
                    <p>Method 3:By using formula tool 
                        Go to view->Formulas->Financial ->IRR 
                        There a dialogue box appears and select the cells  containing respective data 
                        Click ok after entering all the details. </p>

            </div>
        </div>
        <div class="experiment">
            <button class="experiment-btn" onclick="toggleExperiment(7)">Experiment 7</button>
            <div class="experiment-content" id="experiment7">
                <p><strong>Step 1:</strong> Open MS Excel and create a new spreadsheet</p>
                <p><strong>Step 2:</strong> Note down given information in cells</p>
                <p><strong>Step 3:</strong> Calculate below using:</p>
                <p>Method 1: Mathematical formulas: 
                    Payback period: Initial investment/Cash flow 
                    Where P:Principle amount  </p>
                <p>Method 2:By using financial formula: 
                    =PBP(nper,rate,pmt,,type) 
                    Select the cells containing above data 
                    Click on enter  </p>
                    <p>Method 3:By using formula tool 
                        Go to view->Formulas->Financial ->PBP 
                        There a dialogue box appears and select the cells  containing respective data 
                        Click ok after entering all the details.  </p>

            </div>
        </div>
        <div class="experiment">
            <button class="experiment-btn" onclick="toggleExperiment(8)">Experiment 8</button>
            <div class="experiment-content" id="experiment8">
                <p><strong>Step 1:</strong> Open MS Excel and create a new spreadsheet</p>
                <p><strong>Step 2:</strong> Note down given information in cells</p>
                <p><strong>Step 3:</strong> Calculate below using:</p>
                <p>Method 1: By using financial formula: 
                    =NPV(nper,rate,pmt,,type) 
                    =PI(nper,rate,pmt,,type) 
                    =IRR(nper,rate,pmt,,type) 
                    =PBP(nper,rate,pmt,,type) 
                    =ARR(nper,rate,pmt,,type) </p>
                

            </div>
        </div>
         <div class="experiment">
            <button class="experiment-btn" onclick="toggleExperiment(9)">Experiment 9</button>
            <div class="experiment-content" id="experiment9">
                <p><strong>Step 1:</strong> Open MS Excel and create a new spreadsheet</p>
                <p><strong>Step 2:</strong> Note down given information in cells</p>
                <p><strong>Step 3:</strong> Calculate below using:</p>
                <p>Method 1: Mathematical formulas: 
                    K=(1(1-t)+1/n(RV-NP))/(1/2(RV-NP))*100 </p>
                

        <!-- Add Experiment 4 to 10 here using the same format -->
        
    </div>
</div>
<div class="experiment">
    <button class="experiment-btn" onclick="toggleExperiment(10)">Experment 10</button>
    <div class="experiment-content" id="experiment10">
        <p><strong>Step 1:</strong> Open MS Excel and create a new spreadsheet</p>
        <p><strong>Step 2:</strong> Note down given information in cells</p>
        <p><strong>Step 3:</strong> Calculate below using:</p>
        <p>Method 1: Mathematical formulas: 
            FV=(1+r)*P((1+r)^n-1/r) 
            Where P:Principle amount</p>
        <p>Method 2: By using financial formula:=FV(nper,rate,pmt,,type) 
            Select the cells containing above data 
            Click on enter </p>
            <p>Method 3: By using formula tool 
                Go to view->Formulas->Financial ->FV 
                There a dialogue box appears and select the cells  containing respective data 
                Click ok after entering all the details </p>
            
    
    </div>
</div>


<script src="script.js"></script>
</body>
</html>
