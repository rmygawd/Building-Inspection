<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <!-- Ensures mobile-friendly scaling -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Building Inspection Form</title>
  <style>
    :root {
      --primary-color: #000;         /* Black */
      --accent-color: #d11111;       /* Red */
      --background-color: #f7f7f7;   /* Light gray background */
      --text-color: #333;
      --border-radius: 6px;
    }

    body {
      margin: 0;
      padding: 0;
      font-family: "Arial", sans-serif;
      background-color: var(--background-color);
      color: var(--text-color);
    }

    header {
      background-color: var(--primary-color);
      color: #fff;
      padding: 1rem;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 1.5rem;
    }

    .container {
      max-width: 600px;
      margin: 1rem auto;
      padding: 1rem;
      background-color: #fff;
      border-radius: var(--border-radius);
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
    }

    .section {
      margin-bottom: 1.5rem;
    }

    .section h2 {
      background-color: var(--accent-color);
      color: #fff;
      margin-top: 0;
      margin-bottom: 0.5rem;
      padding: 0.5rem;
      border-radius: var(--border-radius);
      font-size: 1.1rem;
    }

    label {
      display: block;
      margin-bottom: 0.5rem;
      font-weight: 500;
    }

    input[type="text"],
    input[type="date"],
    textarea,
    select {
      width: 100%;
      padding: 0.5rem;
      margin-bottom: 1rem;
      border: 1px solid #ccc;
      border-radius: var(--border-radius);
      font-size: 0.9rem;
    }

    input[type="file"] {
      margin-bottom: 1rem;
      font-size: 0.9rem;
      border: none;
    }

    .btn-container {
      display: flex;
      justify-content: space-between;
      gap: 1rem;
      margin-top: 1.5rem;
    }

    button {
      flex: 1;
      padding: 0.8rem;
      background-color: var(--accent-color);
      color: #fff;
      font-size: 1rem;
      font-weight: 600;
      border: none;
      border-radius: var(--border-radius);
      cursor: pointer;
      text-align: center;
    }

    button:hover {
      background-color: #a00; /* Darker red on hover */
    }

    /* Responsive adjustments */
    @media (max-width: 600px) {
      .container {
        margin: 0.5rem;
        padding: 1rem;
      }
      header h1 {
        font-size: 1.25rem;
      }
      .btn-container {
        flex-direction: column;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>Building Inspection Form</h1>
  </header>

  <div class="container">
    <form id="inspection-form">
      <!-- General Information Section -->
      <div class="section">
        <h2>General Information</h2>
        <label for="inspector">
          Inspector Name:
          <input type="text" id="inspector" name="inspector" required />
        </label>
        <label for="date">
          Inspection Date:
          <input type="date" id="date" name="date" required />
        </label>
        <label for="customer-name">
          Customer Name:
          <input type="text" id="customer-name" name="customer-name" required />
        </label>
        <label for="customer-contact">
          Customer Contact:
          <input type="text" id="customer-contact" name="customer-contact" required />
        </label>
        <label for="location-address">
          Location Address:
          <input type="text" id="location-address" name="location-address" required />
        </label>
      </div>

      <!-- Exterior Inspection Section -->
      <div class="section">
        <h2>Exterior Inspection</h2>
        <label for="foundation-condition">
          Foundation Condition:
          <select id="foundation-condition" name="foundation-condition">
            <option value="good">Good</option>
            <option value="fair">Fair</option>
            <option value="poor">Poor</option>
          </select>
        </label>
        <label for="parking-lot">
          Parking Lot Condition:
          <textarea id="parking-lot" name="parking-lot" rows="3"></textarea>
        </label>
        <label for="parking-photos">
          Upload Photos:
          <input
            type="file"
            id="parking-photos"
            name="parking-photos"
            accept="image/*"
            capture="camera"
            multiple
          />
        </label>
      </div>

      <!-- Interior Inspection Section -->
      <div class="section">
        <h2>Interior Inspection</h2>
        <label for="floor-condition">
          Floor Condition:
          <textarea id="floor-condition" name="floor-condition" rows="3"></textarea>
        </label>
        <label for="walls-ceilings">
          Walls & Ceilings Condition:
          <textarea id="walls-ceilings" name="walls-ceilings" rows="3"></textarea>
        </label>
        <label for="interior-photos">
          Upload Photos:
          <input
            type="file"
            id="interior-photos"
            name="interior-photos"
            accept="image/*"
            capture="camera"
            multiple
          />
        </label>
      </div>

      <!-- Mechanical Systems Section -->
      <div class="section">
        <h2>Mechanical Systems</h2>
        <label for="hvac-issues">
          HVAC Issues:
          <textarea id="hvac-issues" name="hvac-issues" rows="3"></textarea>
        </label>
        <label for="plumbing-issues">
          Plumbing Issues:
          <textarea id="plumbing-issues" name="plumbing-issues" rows="3"></textarea>
        </label>
        <label for="mechanical-photos">
          Upload Photos:
          <input
            type="file"
            id="mechanical-photos"
            name="mechanical-photos"
            accept="image/*"
            capture="camera"
            multiple
          />
        </label>
      </div>

      <!-- Summary and Recommendations Section -->
      <div class="section">
        <h2>Summary & Recommendations</h2>
        <label for="immediate-repairs">
          Immediate Repairs:
          <textarea id="immediate-repairs" name="immediate-repairs" rows="3"></textarea>
        </label>
        <label for="long-term">
          Long-Term Considerations:
          <textarea id="long-term" name="long-term" rows="3"></textarea>
        </label>

      <!-- Button container -->
      <div class="btn-container">
        <!-- Normal form submission (if you have a back-end) -->
        <button type="submit">Submit Form</button>

        <!-- Button to generate PDF in a new tab, with "Open In..." option on iOS -->
        <button id="open-in-pdf">Preview PDF</button>
      </div>
    </form>
  </div>

  <!-- Include jsPDF (uses a public CDN link) -->
  <script src="https://cdn.jsdelivr.net/npm/jspdf@latest/dist/jspdf.umd.min.js"></script>
  <script>
    // We attach a click event to the "Preview PDF" button
    const pdfBtn = document.getElementById("open-in-pdf");
    pdfBtn.addEventListener("click", function (event) {
      event.preventDefault(); // Prevent form submission

      const { jsPDF } = window.jspdf;
      const doc = new jsPDF();

      // Gather form data
      const inspector = document.getElementById("inspector").value;
      const date = document.getElementById("date").value;
      const customerName = document.getElementById("customer-name").value;
      const customerContact = document.getElementById("customer-contact").value;
      const locationAddress = document.getElementById("location-address").value;

      const foundation = document.getElementById("foundation-condition").value;
      const parkingLot = document.getElementById("parking-lot").value;
      const floorCondition = document.getElementById("floor-condition").value;
      const wallsCeilings = document.getElementById("walls-ceilings").value;
      const hvacIssues = document.getElementById("hvac-issues").value;
      const plumbingIssues = document.getElementById("plumbing-issues").value;
      const immediateRepairs = document.getElementById("immediate-repairs").value;
      const longTerm = document.getElementById("long-term").value;

      // Simple formatting in the PDF
      // You can customize spacing, font sizes, or add images/logos as needed
      doc.setFontSize(14);
      doc.text("Building Inspection", 10, 10);

      doc.setFontSize(12);
      let yPos = 20;
      
      doc.text(`Inspector Name: ${inspector}`, 10, yPos); 
      yPos += 10;
      doc.text(`Inspection Date: ${date}`, 10, yPos);
      yPos += 10;
      doc.text(`Customer Name: ${customerName}`, 10, yPos);
      yPos += 10;
      doc.text(`Customer Contact: ${customerContact}`, 10, yPos);
      yPos += 10;
      doc.text(`Location Address: ${locationAddress}`, 10, yPos);
      yPos += 15;

      doc.text("Exterior Inspection:", 10, yPos);
      yPos += 10;
      doc.text(`Foundation Condition: ${foundation}`, 10, yPos);
      yPos += 10;
      doc.text(`Parking Lot Condition: ${parkingLot}`, 10, yPos);
      yPos += 15;

      doc.text("Interior Inspection:", 10, yPos);
      yPos += 10;
      doc.text(`Floor Condition: ${floorCondition}`, 10, yPos);
      yPos += 10;
      doc.text(`Walls & Ceilings: ${wallsCeilings}`, 10, yPos);
      yPos += 15;

      doc.text("Mechanical Systems:", 10, yPos);
      yPos += 10;
      doc.text(`HVAC Issues: ${hvacIssues}`, 10, yPos);
      yPos += 10;
      doc.text(`Plumbing Issues: ${plumbingIssues}`, 10, yPos);
      yPos += 15;

      doc.text("Summary & Recommendations:", 10, yPos);
      yPos += 10;
      doc.text(`Immediate Repairs: ${immediateRepairs}`, 10, yPos);
      yPos += 10;
      doc.text(`Long-Term Considerations: ${longTerm}`, 10, yPos);
      yPos += 15;

      // Open PDF in a new browser tab (iOS Chrome can use "Open In..." from here)
      doc.output("dataurlnewwindow");
    });
  </script>
</body>
</html>