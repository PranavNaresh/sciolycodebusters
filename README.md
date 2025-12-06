<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Science Olympiad Codebusters</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    :root {
      --bg: #050816;
      --card: #0f172a;
      --accent: #38bdf8;
      --accent-soft: #1d4ed8;
      --text: #e5e7eb;
      --muted: #9ca3af;
    }
    * { box-sizing: border-box; }
    body {
      margin: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      background: radial-gradient(circle at top, #1d2545, #020617 55%);
      color: var(--text);
      line-height: 1.6;
    }
    header {
      padding: 3rem 1.5rem 2rem;
      text-align: center;
      background: radial-gradient(circle at top, #1e293b, #020617);
      border-bottom: 1px solid #1f2937;
    }
    header h1 {
      font-size: clamp(2.3rem, 4vw, 3rem);
      margin: 0 0 0.5rem;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      background: linear-gradient(to right, #38bdf8, #a855f7, #f97316);
      -webkit-background-clip: text;
      color: transparent;
    }
    header p {
      max-width: 700px;
      margin: 0.25rem auto 1.75rem;
      color: var(--muted);
      font-size: 0.98rem;
    }
    .tagline {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      padding: 0.3rem 0.75rem;
      border-radius: 999px;
      border: 1px solid rgba(148,163,184,0.5);
      background: rgba(15,23,42,0.8);
      color: var(--muted);
      font-size: 0.8rem;
      margin-bottom: 0.75rem;
    }
    .tagline span.key {
      width: 11px;
      height: 11px;
      border-radius: 999px;
      background: radial-gradient(circle at 30% 30%, #e5e7eb, #22c55e);
      box-shadow: 0 0 10px rgba(34,197,94,0.8);
    }
    .container {
      max-width: 1000px;
      margin: 0 auto;
      padding: 1.5rem;
    }
    section {
      margin-bottom: 2rem;
    }
    .card {
      background: linear-gradient(135deg, rgba(15,23,42,0.96), rgba(15,23,42,0.95));
      border-radius: 0.9rem;
      padding: 1.25rem 1.4rem;
      border: 1px solid rgba(31,41,55,0.9);
      box-shadow: 0 18px 40px rgba(15,23,42,0.9);
      position: relative;
      overflow: hidden;
    }
    .card::before {
      content: "";
      position: absolute;
      inset: -40%;
      background: radial-gradient(circle at top left, rgba(56,189,248,0.08), transparent 60%);
      opacity: 0.9;
      pointer-events: none;
    }
    h2 {
      font-size: 1.25rem;
      margin: 0 0 0.5rem;
      display: inline-flex;
      align-items: center;
      gap: 0.45rem;
      letter-spacing: 0.02em;
      text-transform: uppercase;
      font-weight: 600;
    }
    h2 .pill {
      font-size: 0.7rem;
      padding: 0.1rem 0.5rem;
      border-radius: 999px;
      border: 1px solid rgba(148,163,184,0.7);
      color: var(--muted);
    }
    h3 {
      margin: 1.1rem 0 0.3rem;
      font-size: 1.02rem;
      color: #e5e7eb;
    }
    p {
      margin: 0.2rem 0 0.6rem;
      font-size: 0.95rem;
    }
    ul {
      margin: 0.4rem 0 0.5rem 1.1rem;
      padding: 0;
      font-size: 0.93rem;
    }
    li { margin-bottom: 0.28rem; }
    a {
      color: var(--accent);
      text-decoration: none;
    }
    a:hover {
      color: #a5b4fc;
      text-decoration: underline;
    }
    .grid {
      display: grid;
      grid-template-columns: minmax(0, 1.1fr) minmax(0, 1.1fr);
      gap: 1.3rem;
    }
    .chip-row {
      display: flex;
      flex-wrap: wrap;
      gap: 0.35rem;
      margin-top: 0.3rem;
    }
    .chip {
      font-size: 0.7rem;
      padding: 0.18rem 0.55rem;
      border-radius: 999px;
      border: 1px solid rgba(148,163,184,0.6);
      color: var(--muted);
      background: rgba(15,23,42,0.85);
    }
    .kbd-row {
      display: flex;
      flex-wrap: wrap;
      gap: 0.3rem;
      margin-top: 0.4rem;
    }
    .kbd {
      font-family: "JetBrains Mono", ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
      font-size: 0.74rem;
      padding: 0.22rem 0.5rem;
      border-radius: 0.45rem;
      border: 1px solid rgba(75,85,99,0.9);
      background: radial-gradient(circle at top, #1f2937, #020617);
      color: #e5e7eb;
      letter-spacing: 0.05em;
    }
    .table-wrap {
      margin-top: 0.5rem;
      overflow-x: auto;
    }
    table {
      border-collapse: collapse;
      width: 100%;
      font-size: 0.86rem;
      background: rgba(15,23,42,0.96);
    }
    th, td {
      border: 1px solid rgba(55,65,81,0.9);
      padding: 0.4rem 0.55rem;
      text-align: left;
    }
    th {
      background: rgba(15,23,42,0.95);
      font-weight: 600;
      font-size: 0.8rem;
      text-transform: uppercase;
      letter-spacing: 0.06em;
      color: var(--muted);
    }
    tr:nth-child(even) td {
      background: rgba(15,23,42,0.9);
    }
    .footer {
      text-align: center;
      padding: 1.75rem 1.5rem 2.25rem;
      color: var(--muted);
      font-size: 0.8rem;
    }
    .footer span {
      color: var(--accent);
    }
    @media (max-width: 768px) {
      header { padding: 2.4rem 1.1rem 1.6rem; }
      .container { padding: 1.1rem; }
      .grid { grid-template-columns: minmax(0, 1fr); }
      .card { padding: 1.05rem 1.05rem; }
    }
  </style>
</head>
<body>
  <header>
    <div class="tagline">
      <span class="key"></span>
      <span>Science Olympiad &bull; Codebusters</span>
    </div>
    <h1>Crack the Code, Win the Event</h1>
    <p>
      Codebusters is a Science Olympiad event where teams decrypt and sometimes encrypt secret messages
      using classic and modern ciphers, problem‑solving skills, and teamwork under time pressure.
    </p>
  </header>

  <main class="container">
    <section>
      <div class="card">
        <h2>
          Event overview
          <span class="pill">What is Codebusters?</span>
        </h2>
        <p>
          Codebusters challenges a team to decode encrypted messages using logic, pattern recognition,
          and knowledge of a set list of ciphers from the official rules for the season.[web:3][web:6]
        </p>
        <p>
          Teams usually consist of up to three students who work together on a written test that may
          include a timed cryptogram, substitution ciphers, arithmetic‑style cryptarithms, and other
          formats specified by the current rules.[web:3][web:7]
        </p>

        <h3>Typical ciphers you may see</h3>
        <ul>
          <li>Simple substitution: Aristocrat and Patristocrat style letter‑substitution puzzles.[web:3][web:8]</li>
          <li>Caesar and affine shifts: Alphabet shifting with fixed or linear rules.[web:3]</li>
          <li>Vigenère cipher: Polyalphabetic substitution using a repeating key word.[web:3]</li>
          <li>Symbol ciphers: Pigpen, Dancing Men, and other symbol‑based encodings in some divisions.[web:6][web:10]</li>
          <li>Tap or grid ciphers: Representing letters using positions in a grid or tap patterns.[web:6][web:10]</li>
          <li>Cryptarithms: Arithmetic puzzles where digits are replaced by letters.[web:9]</li>
        </ul>

        <div class="chip-row">
          <span class="chip">Logic + Patterns</span>
          <span class="chip">Teamwork</span>
          <span class="chip">Speed</span>
          <span class="chip">Attention to detail</span>
        </div>
      </div>
    </section>

    <section>
      <div class="grid">
        <div class="card">
          <h2>
            Rules and format
            <span class="pill">How the test works</span>
          </h2>
          <p>
            The official Codebusters rules are published each season by Science Olympiad and describe
            allowed ciphers, resources, and the exact scoring system for that year.[web:3][web:7]
          </p>
          <p>
            Teams start together when the supervisor gives the signal and work on a packet of questions,
            often including one specially marked timed cryptogram that must be solved as fast and accurately
            as possible for a bonus.[web:7]
          </p>

          <h3>General competition guidelines</h3>
          <ul>
            <li>Follow the current year’s national or state rules for your division and tournament level.[web:3][web:7]</li>
            <li>Only materials specified in the rules (such as pencils and non‑programmable calculators) are allowed.[web:7]</li>
            <li>Event supervisors usually provide scratch paper and, in some formats, a resource sheet with tables or letter frequencies.[web:3][web:6]</li>
            <li>Students may divide the test pages and work on different cipher types in parallel.</li>
          </ul>
        </div>

        <div class="card">
          <h2>
            Scoring
            <span class="pill">How to earn points</span>
          </h2>
          <p>
            Many Codebusters tests assign point values that increase with difficulty, from easier substitution
            questions to very challenging multi‑step or long‑text ciphers.[web:8][web:7]
          </p>
          <p>
            Final scores often combine the total points from all questions with a timing bonus based on how
            quickly the designated timed cryptogram is solved, with penalties for incorrect letters.[web:7][web:8]
          </p>

          <div class="table-wrap">
            <table>
              <thead>
                <tr>
                  <th>Aspect</th>
                  <th>Typical approach</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>Question points</td>
                  <td>Higher point values for longer or more complex ciphers, lower for short or guided ones.[web:8]</td>
                </tr>
                <tr>
                  <td>Letter accuracy</td>
                  <td>Full credit for answers with few or no errors; additional errors can reduce the score for that item.[web:7]</td>
                </tr>
                <tr>
                  <td>Timing bonus</td>
                  <td>Extra points for solving the first cryptogram quickly; slower solutions or timeouts reduce or eliminate the bonus.[web:7]</td>
                </tr>
                <tr>
                  <td>Tie breakers</td>
                  <td>Selected questions are sometimes used to break ties by comparing scores or degree of correctness.[web:7]</td>
                </tr>
              </tbody>
            </table>
          </div>

          <div class="kbd-row">
            <span class="kbd">FREQ</span>
            <span class="kbd">ETAOIN SHRDLU</span>
            <span class="kbd">PATTERNS</span>
            <span class="kbd">TIMING</span>
          </div>
        </div>
      </div>
    </section>

    <section>
      <div class="card">
        <h2>
          Strategy and tips
          <span class="pill">Compete like a pro</span>
        </h2>
        <h3>During the event</h3>
        <ul>
          <li>Assign roles so one teammate focuses on the timed problem while others start other ciphers.</li>
          <li>Use frequency analysis for long substitution ciphers and look for common short words like “THE” or “AND”.[web:3][web:8]</li>
          <li>Mark guesses lightly and update consistently; one wrong mapping can corrupt an entire answer.</li>
          <li>Keep an eye on the clock and leave time to copy final answers clearly onto the answer sheet.</li>
        </ul>

        <h3>Practice ideas</h3>
        <ul>
          <li>Drill letter frequencies, common patterns, and cipher‑specific tricks until they become automatic.[web:3][web:8]</li>
          <li>Simulate full tests with a strict time limit to get used to pacing.[web:4][web:9]</li>
          <li>Rotate roles within your team so everyone gets experience on different cipher types and the timed question.[web:6]</li>
        </ul>
      </div>
    </section>

    <section>
      <div class="card">
        <h2>
          Practice resources
          <span class="pill">Where to train</span>
        </h2>
        <p>
          Always verify that resources match the current season’s rules, because allowed ciphers or formats
          can change between years.[web:3]
        </p>
        <ul>
          <li>
            Official Science Olympiad Codebusters event page for rules, clarifications, and example materials.[web:3]
          </li>
          <li>
            Online Codebusters test builders and sample tests that let you generate practice sets and past exams.[web:4][web:9]
          </li>
          <li>
            State and regional Science Olympiad organizations that sometimes post training slides or elementary versions of the event.[web:6][web:10][web:11]
          </li>
          <li>
            Community‑run guides and collections of recommended websites that highlight popular practice tools.[web:5]
          </li>
        </ul>
      </div>
    </section>
  </main>

  <div class="footer">
    <p>
      Not an official Science Olympiad site. Always follow the current <span>Rules Manual</span> and any
      clarifications published for your tournament.[web:3]
    </p>
  </div>
</body>
</html>
