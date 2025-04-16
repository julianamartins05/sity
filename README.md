from zipfile import ZipFile
import os

# Criar estrutura dos arquivos
html_content = """<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Meu Site</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <div class="logo">LOGO</div>
    <nav>
      <ul>
        <li><a href="#">HOME</a></li>
        <li><a href="#">SOBRE</a></li>
        <li><a href="#">CONTATO</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section class="linha">
      <div class="caixa">IMAGEM</div>
      <div class="caixa">TEXTO</div>
    </section>
    <section class="linha">
      <div class="caixa grande">TEXTO</div>
      <div class="caixa grande">IMAGEM</div>
    </section>
  </main>

  <footer>
    TODO OS DIREITOS RESERVADO
  </footer>
</body>
</html>
"""

css_content = """body {
  margin: 0;
  font-family: Arial, sans-serif;
}

header {
  background-color: #d9d9d9;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 30px;
}

.logo {
  font-weight: bold;
}

nav ul {
  list-style: none;
  display: flex;
  gap: 20px;
  margin: 0;
  padding: 0;
}

nav ul li a {
  text-decoration: none;
  color: #000;
}

main {
  padding: 40px;
}

.linha {
  display: flex;
  justify-content: space-between;
  margin-bottom: 30px;
  flex-wrap: wrap;
}

.caixa {
  background-color: #d9d9d9;
  width: 45%;
  height: 150px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.caixa.grande {
  width: 45%;
  height: 200px;
}

footer {
  background-color: #d9d9d9;
  text-align: center;
  padding: 15px;
  font-size: 14px;
}
"""

# Caminho temporário dos arquivos
html_path = "/mnt/data/index.html"
css_path = "/mnt/data/style.css"
zip_path = "/mnt/data/site_simples.zip"

# Salvar os arquivos
with open(html_path, "w", encoding="utf-8") as f:
    f.write(html_content)

with open(css_path, "w", encoding="utf-8") as f:
    f.write(css_content)

# Criar arquivo zip
with ZipFile(zip_path, 'w') as zipf:
    zipf.write(html_path, arcname="index.html")
    zipf.write(css_path, arcname="style.css")

zip_path
