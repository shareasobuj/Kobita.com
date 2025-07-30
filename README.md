 Kobita.com

<html lang="bn">
<head>
  <meta charset="UTF-8">
  <title>🌸 আমার কবিতার বই 🌸</title>
  <style>
    body {
      font-family: 'Siyam Rupali', sans-serif;
      margin: 0;
      padding: 0;
      background: #fff9f0;
      color: #333;
    }

    header {
      background-color: #ffcccb;
      text-align: center;
      padding: 20px;
    }

    header h1 {
      margin: 0;
      font-size: 2rem;
    }

    main {
      padding: 20px;
    }

    .poem-list ul {
      list-style-type: none;
      padding: 0;
    }

    .poem-list li {
      background: #f2f2f2;
      margin: 10px 0;
      padding: 10px;
      cursor: pointer;
      border-radius: 5px;
      transition: background 0.3s;
    }

    .poem-list li:hover {
      background: #ffe4e1;
    }

    .poem {
      margin-top: 30px;
      padding: 20px;
      background: #fff5f5;
      border-radius: 10px;
    }

    .buttons {
      margin-top: 15px;
    }

    button {
      padding: 10px;
      margin-right: 10px;
      border: none;
      background-color: #ff9999;
      color: white;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background-color: #e06666;
    }

    footer {
      text-align: center;
      padding: 10px;
      background: #ffdcdc;
      margin-top: 40px;
    }
  </style>
</head>
<body>
  <header>
    <h1>🌸 আমার কবিতার বই 🌸</h1>
    <p>লেখক: শারেয়া সবুজ</p>
  </header>

  <main>
    <section class="poem-list">
      <h2>📖 কবিতার তালিকা</h2>
      <ul>
        <li onclick="showPoem(0)">১. শিশির ভেজা ভোর</li>
        <li onclick="showPoem(1)">২. নদীর ডাক</li>
        <li onclick="showPoem(2)">৩. ভালোবাসার ছায়া</li>
        <li onclick="showPoem(3)">৪. গ্রাম বাংলার গন্ধ</li>
        <li onclick="showPoem(4)">৫. রাতের আকাশ</li>
      </ul>
    </section>

    <section id="poem-display" class="poem">
      <h3>কবিতা এখানে দেখানো হবে</h3>
      <p>একটি কবিতা দেখতে উপরের তালিকা থেকে একটি কবিতা নির্বাচন করুন।</p>
      <div class="buttons" style="display:none;" id="action-buttons">
        <button onclick="printPoem()">🖨️ প্রিন্ট করুন</button>
        <button onclick="downloadPDF()">⬇️ PDF ডাউনলোড</button>
      </div>
    </section>
  </main>

  <footer>
    <p>© 2025 | সব কবিতার স্বত্ব محفوظ</p>
  </footer>

  <!-- jsPDF CDN -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

  <script>
    const poems = [
      {
        title: "শিশির ভেজা ভোর",
        content: `ভোরের শিশিরে জড়ানো ঘাস,  
পায়ে লাগলে শীতল আভাস।  
সূর্য উঠছে, চোখে আলো,  
নতুন দিনের মধুর গালো।  
চড়ুই পাখির গান বাজে,  
ফুলের ঘ্রাণে মন সাজে।  
নতুন আশা জাগে প্রাণে,  
ভোরের রঙে রাঙা জানে।`
      },
      {
        title: "নদীর ডাক",
        content: `নদী ডাকে, কূলে বসে শুনি,  
জলের সুরে হারাই আমি ধুনি।  
তার ঢেউ যেন সুরের পাখা,  
মন ভাসে, জলের গান আঁকা।  
নৌকা চলে ছলাৎ শব্দে,  
মেঘ ছুঁয়ে চলে ঢেউয়ের মধ্যে।  
চির চেনা সেই নদী পথ,  
মনে গেঁথে রেখেছে যত।`
      },
      {
        title: "ভালোবাসার ছায়া",
        content: `তোমার ছায়ায় ছিলাম আমি,  
নরম চোখে কাঁপে নামি।  
ভালোবাসার সুরে বাজে,  
হৃদয়খানি মনের মাঝে।  
তোমার হাসি, তপ্ত ভাষা,  
মুছে দেয় সব কষ্ট আশা।  
চিরকাল তুমিই আমার,  
ভালোবাসার নিঃশ্বাস ধার।`
      },
      {
        title: "গ্রাম বাংলার গন্ধ",
        content: `কাদামাটির পথ বেয়ে হেঁটে,  
জীবন কাটে ধীরে ধীরে মেটে।  
ধানক্ষেতে বাজে বায়ুর সুর,  
মাঠে মেঘে জোনাকির নূর।  
গরুর গাড়ি, শিশির ভোর,  
প্রকৃতিতে মিশে যায় মন ভোর।  
পাখির কলতানে শুরু সকাল,  
এই বাংলাই আমার ভাল।`
      },
      {
        title: "রাতের আকাশ",
        content: `আকাশ জুড়ে নক্ষত্র মেলে,  
চাঁদটা হাসে দিগন্ত খেলায়।  
রাতের নীরবতা কথা বলে,  
স্বপ্নেরা আসে মনে এক ঢলায়।  
ঝিকিমিকি তারা করে ডাক,  
ঘুমিয়ে পড়ে শহরের ছায়া।  
রাতের রংয়ে আঁকা ব্যথা,  
তারাই তো দেয় জীবনের প্রয়াস।`
      }
    ];

    let currentPoem = null;

    function showPoem(index) {
      const poem = poems[index];
      currentPoem = poem;

      const display = document.getElementById("poem-display");
      const buttons = document.getElementById("action-buttons");

      display.innerHTML = `
        <h3>${poem.title}</h3>
        <p>${poem.content.replace(/\n/g, "<br>")}</p>
      `;
      display.appendChild(buttons);
      buttons.style.display = "block";
    }

    function printPoem() {
      if (!currentPoem) return;
      const printWindow = window.open('', '', 'width=800,height=600');
      printWindow.document.write(`<html><head><title>${currentPoem.title}</title></head><body>`);
      printWindow.document.write(`<h2>${currentPoem.title}</h2><pre>${currentPoem.content}</pre>`);
      printWindow.document.write('</body></html>');
      printWindow.document.close();
      printWindow.print();
    }

    async function downloadPDF() {
      if (!currentPoem) return;
      const { jsPDF } = window.jspdf;
      const doc = new jsPDF();
      doc.setFont("Helvetica");
      doc.setFontSize(16);
      doc.text(currentPoem.title, 20, 20);
      doc.setFontSize(12);
      const lines = doc.splitTextToSize(currentPoem.content, 170);
      doc.text(lines, 20, 30);
      doc.save(`${currentPoem.title}.pdf`);
    }
  </script>

