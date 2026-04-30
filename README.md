import os

# Definindo o conteúdo HTML e CSS para o marketplace agrícola
html_content = """
<!DOCTYPE html>
<html lang="pt-PT">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AgroDirecto - Do Campo à Mesa</title>
    <style>
        :root {
            --primary: #2d5a27;
            --secondary: #f4b400;
            --light: #f8f9fa;
            --dark: #333;
            --accent: #e67e22;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #fff;
            color: var(--dark);
            line-height: 1.6;
        }

        header {
            background: white;
            padding: 1rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--primary);
        }

        nav a {
            margin-left: 20px;
            text-decoration: none;
            color: var(--dark);
            font-weight: 500;
        }

        .hero {
            background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), 
                        url('https://images.unsplash.com/photo-1500382017468-9049fed747ef?auto=format&fit=crop&w=1600&q=80');
            background-size: cover;
            background-position: center;
            height: 60vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
            padding: 0 20px;
        }

        .hero h1 { font-size: 3rem; margin-bottom: 1rem; }
        .hero p { font-size: 1.2rem; margin-bottom: 2rem; max-width: 600px; }

        .btn {
            background: var(--secondary);
            color: var(--dark);
            padding: 12px 30px;
            text-decoration: none;
            border-radius: 5px;
            font-weight: bold;
            transition: 0.3s;
        }

        .btn:hover { background: var(--accent); color: white; }

        .section-title {
            text-align: center;
            margin: 40px 0;
            font-size: 2rem;
            color: var(--primary);
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px;
            padding: 0 5%;
            margin-bottom: 50px;
        }

        .product-card {
            border: 1px solid #ddd;
            border-radius: 10px;
            overflow: hidden;
            transition: transform 0.3s;
        }

        .product-card:hover { transform: translateY(-5px); box-shadow: 0 10px 20px rgba(0,0,0,0.1); }

        .product-image {
            height: 200px;
            background-size: cover;
            background-position: center;
            position: relative;
        }

        .origin-tag {
            position: absolute;
            bottom: 10px;
            left: 10px;
            background: rgba(45, 90, 39, 0.9);
            color: white;
            padding: 5px 10px;
            font-size: 0.8rem;
            border-radius: 3px;
        }

        .product-info { padding: 20px; }
        .product-info h3 { margin-bottom: 10px; }
        .price { color: var(--primary); font-weight: bold; font-size: 1.2rem; }

        .qr-section {
            background: var(--light);
            padding: 60px 5%;
            display: flex;
            align-items: center;
            flex-wrap: wrap;
            gap: 40px;
        }

        .qr-text { flex: 1; min-width: 300px; }
        .qr-image { flex: 1; text-align: center; }
        .qr-image img { max-width: 200px; border: 10px solid white; box-shadow: 0 0 20px rgba(0,0,0,0.1); }

        footer {
            background: var(--primary);
            color: white;
            padding: 40px 5%;
            text-align: center;
        }

        @media (max-width: 768px) {
            .hero h1 { font-size: 2rem; }
            nav { display: none; }
        }
    </style>
</head>
<body>

<header>
    <div class="logo">AgroDirecto</div>
    <nav>
        <a href="#">Loja</a>
        <a href="#">Assinaturas</a>
        <a href="#">Produtores</a>
        <a href="#">Rastreio</a>
    </nav>
</header>

<section class="hero">
    <h1>Frescura Real, Direto da Terra</h1>
    <p>Conectamos famílias a produtores locais. Alimentos colhidos no dia e entregues à sua porta com total transparência.</p>
    <a href="#" class="btn">Explorar Cestas de Época</a>
</section>

<h2 class="section-title">Produtos em Destaque</h2>

<div class="products-grid">
    <div class="product-card">
        <div class="product-image" style="background-image: url('https://images.unsplash.com/photo-1518977676601-b53f82aba655?auto=format&fit=crop&w=500&q=80')">
            <span class="origin-tag">📍 Quinta do Vale, Alentejo</span>
        </div>
        <div class="product-info">
            <h3>Batata Doce Bio (2kg)</h3>
            <p>Cultivada sem pesticidas, rica em sabor.</p>
            <div class="price">4,50€</div>
            <br>
            <a href="#" style="color: var(--primary); text-decoration: none; font-size: 0.9rem;">Ver história do produtor →</a>
        </div>
    </div>

    <div class="product-card">
        <div class="product-image" style="background-image: url('https://images.unsplash.com/photo-1598170845058-32b9d6a5da37?auto=format&fit=crop&w=500&q=80')">
            <span class="origin-tag">📍 Hortas de Palmela</span>
        </div>
        <div class="product-info">
            <h3>Cenouras Baby (Maço)</h3>
            <p>Doces e crocantes, perfeitas para snacks.</p>
            <div class="price">2,20€</div>
            <br>
            <a href="#" style="color: var(--primary); text-decoration: none; font-size: 0.9rem;">Ver história do produtor →</a>
        </div>
    </div>

    <div class="product-card">
        <div class="product-image" style="background-image: url('https://images.unsplash.com/photo-1560806117-2868631c5831?auto=format&fit=crop&w=500&q=80')">
            <span class="origin-tag">📍 Pomar do Sr. Manuel, Alcobaça</span>
        </div>
        <div class="product-info">
            <h3>Maçã Alcobaça IGP (1kg)</h3>
            <p>O equilíbrio perfeito entre acidez e doçura.</p>
            <div class="price">1,95€</div>
            <br>
            <a href="#" style="color: var(--primary); text-decoration: none; font-size: 0.9rem;">Ver história do produtor →</a>
        </div>
    </div>
</div>

<section class="qr-section">
    <div class="qr-text">
        <h2>Transparência via QR Code</h2>
        <p>Todas as nossas embalagens contêm um código único. Ao digitalizar, poderá ver:</p>
        <ul style="margin-top: 15px; margin-left: 20px;">
            <li>Data e hora exata da colheita.</li>
            <li>Análises de solo e água da propriedade.</li>
            <li>Certificados de agricultura biológica.</li>
            <li>Distância percorrida até à sua casa.</li>
        </ul>
    </div>
    <div class="qr-image">
        <img src="https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=https://exemplo-agro.pt/rastreio/quinta-do-vale" alt="Exemplo QR Code">
        <p style="margin-top: 10px; font-size: 0.8rem; color: #666;">Experimente simular o rastreio</p>
    </div>
</section>

<footer>
    <p>&copy; 2026 AgroDirecto - Sustentabilidade e Frescura. Todos os direitos reservados.</p>
</footer>

</body>
</html>
"""

# Guardando o arquivo
with open("marketplace_agro.html", "w", encoding="utf-8") as f:
    f.write(html_content)
