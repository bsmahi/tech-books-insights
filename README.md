<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Knowledge Hub</title>
<style>
  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: #f5f5f5;
    margin: 0;
    padding: 0;
    line-height: 1.6;
  }
  header {
    background: #4CAF50;
    color: white;
    text-align: center;
    padding: 2rem 1rem;
  }
  header h1 {
    margin: 0;
    font-size: 2rem;
  }
  header p {
    font-style: italic;
    font-size: 1rem;
    margin-top: 0.5rem;
  }
  .container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding: 2rem 1rem;
    gap: 1rem;
  }
  .card {
    background: white;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    padding: 1rem 1.5rem;
    width: 280px;
    transition: transform 0.2s;
  }
  .card:hover {
    transform: translateY(-5px);
  }
  details {
    margin-top: 1rem;
  }
  summary {
    font-weight: bold;
    cursor: pointer;
    font-size: 1.1rem;
  }
  a {
    text-decoration: none;
    color: #4CAF50;
  }
  a:hover {
    text-decoration: underline;
  }
  .badge {
    background: #4CAF50;
    color: white;
    padding: 2px 6px;
    font-size: 0.8rem;
    border-radius: 5px;
    margin-left: 0.5rem;
  }
</style>
</head>
<body>

<header>
  <h1>💡 Knowledge Hub</h1>
  <p>"The more I learn, the more I realize how much I don't know." — Albert Einstein</p>
</header>

<div class="container">

  <div class="card">
    <details>
      <summary>🔗 Important Links</summary>
      <ul>
        <li><a href="./ImportantLinks.md">📌 Important Links</a></li>
      </ul>
    </details>
  </div>

  <div class="card">
    <details>
      <summary>🧮 Mathematics</summary>
      <ul>
        <li><a href="./MathsLinks.md">📘 Maths Links</a></li>
      </ul>
    </details>
  </div>

  <div class="card">
    <details>
      <summary>🏛 Architecture</summary>
      <ul>
        <li><a href="https://www.infoq.com/articles/architecture-experimentation">📝 Software Architecture and the Art of Experimentation</a></li>
        <li><a href="./ArchitecturePatterns/SoftwareArchitectureStyles.pdf">📄 Software Architecture Styles</a></li>
        <li><a href="./ArchitecturePatterns/event-driven-architecture.md">⚡ Event Driven Architecture</a></li>
      </ul>
    </details>
  </div>

  <div class="card">
    <details>
      <summary>🌱 Spring Framework</summary>
      <ul>
        <li><a href="./spring/SpringNotes.md">📖 Spring Essentials</a></li>
      </ul>
    </details>
  </div>

  <div class="card">
    <details>
      <summary>💻 Computer Science</summary>
      <ul>
        <li><a href="https://www.freecodecamp.org/news/free-courses-top-cs-universities/">🎓 Free Computer Science Courses from the World's Top Universities</a></li>
      </ul>
    </details>
  </div>

  <div class="card">
    <details>
      <summary>☕ Kotlin</summary>
      <ul>
        <li><a href="./kotlin_roadmap.md">🚀 Kotlin RoadMap</a></li>
      </ul>
    </details>
  </div>

</div>

</body>
</html>
