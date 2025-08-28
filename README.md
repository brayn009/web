<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lista de Productos para Vendedores</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            background-color: #eef1f5;
            padding: 20px;
            color: #333;
        }
        .container {
            max-width: 900px;
            margin: auto;
            padding: 20px;
            background-color: #ffffff;
            border-radius: 12px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.1);
        }
        h2 {
            text-align: center;
            color: #1E88E5;
            margin-bottom: 25px;
            font-weight: 500;
        }
        table {
            border-collapse: collapse;
            width: 100%;
            font-size: 14px;
        }
        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid #e0e0e0;
        }
        th {
            background-color: #1E88E5;
            color: white;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        tr:nth-child(even) {
            background-color: #f9f9f9;
        }
        tr:hover {
            background-color: #e0e0e0;
            transition: background-color 0.3s ease;
        }
        td {
            text-align: center;
        }
        td:first-child {
            text-align: left;
        }

        .disponible {
            color: #28a745;
            font-weight: 500;
        }
        .no-disponible {
            color: #dc3545;
            font-weight: 500;
        }

        .search-container {
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        #searchInput {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ccc;
            border-radius: 8px;
            font-size: 16px;
            transition: border-color 0.3s ease;
        }
        #searchInput:focus {
            outline: none;
            border-color: #1E88E5;
            box-shadow: 0 0 5px rgba(30, 136, 229, 0.5);
        }
        .search-label {
            font-weight: 500;
            color: #555;
            font-size: 16px;
        }
        
        .total-container {
            margin-top: 20px;
            margin-bottom: 20px;
            text-align: right;
            font-size: 24px; /* Aumentamos el tamaño para que sea más visible */
            font-weight: 700;
            color: #333;
            padding: 10px 0;
            border-top: 2px solid #1E88E5;
        }

        /* Estilos para el input de cantidad */
        .product-quantity {
            width: 60px;
            text-align: center;
            border: 1px solid #ccc;
            border-radius: 4px;
            padding: 5px;
        }

        /* Estilos responsivos */
        @media (max-width: 768px) {
            table, thead, tbody, th, td, tr {
                display: block;
            }
            thead tr {
                position: absolute;
                top: -9999px;
                left: -9999px;
            }
            tr {
                margin: 0 0 1rem 0;
                border: 1px solid #e0e0e0;
                border-radius: 8px;
            }
            td {
                border: none;
                position: relative;
                padding-left: 50%;
                text-align: right;
            }
            td:before {
                position: absolute;
                top: 0;
                left: 6px;
                width: 45%;
                padding-right: 10px;
                white-space: nowrap;
                text-align: left;
                font-weight: 700;
                color: #555;
            }
            td:nth-of-type(1):before { content: "Producto"; }
            td:nth-of-type(2):before { content: "Cantidad"; }
            td:nth-of-type(3):before { content: "Precio para Vendedores"; }
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Lista de Productos para Vendedores</h2>

        <div class="total-container">
            Total: <span id="totalPrice">$0.00</span>
        </div>
        
        <div class="search-container">
            <label for="searchInput" class="search-label">Buscar producto:</label>
            <input type="text" id="searchInput" placeholder="Escribe el nombre del producto...">
        </div>

        <table class="dataframe" id="productsTable">
            <thead>
                <tr>
                    <th>Producto</th>
                    <th>Cantidad</th>
                    <th>Precio para Vendedores</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Miel Bronqueal</td>
                    <td><input type="number" class="product-quantity" data-price="330.00" value="0" min="0"></td>
                    <td class="price-cell">$330.00</td>
                </tr>
                <tr>
                    <td>Rompe Pecho</td>
                    <td><input type="number" class="product-quantity" data-price="300.00" value="0" min="0"></td>
                    <td class="price-cell">$300.00</td>
                </tr>
                <tr>
                    <td>Berro y Sebolla</td>
                    <td><input type="number" class="product-quantity" data-price="325.00" value="0" min="0"></td>
                    <td class="price-cell">$325.00</td>
                </tr>
                <tr>
                    <td>Rabano Sebolla y Miel</td>
                    <td><input type="number" class="product-quantity" data-price="200.00" value="0" min="0"></td>
                    <td class="price-cell">$200.00</td>
                </tr>
                <tr>
                    <td>Betamil</td>
                    <td><input type="number" class="product-quantity" data-price="210.00" value="0" min="0"></td>
                    <td class="price-cell">$210.00</td>
                </tr>
                <tr>
                    <td>DBT</td>
                    <td><input type="number" class="product-quantity" data-price="190.00" value="0" min="0"></td>
                    <td class="price-cell">$190.00</td>
                </tr>
                <tr>
                    <td>Sacacripe</td>
                    <td><input type="number" class="product-quantity" data-price="325.00" value="0" min="0"></td>
                    <td class="price-cell">$325.00</td>
                </tr>
                <tr>
                    <td>Bromisol</td>
                    <td><input type="number" class="product-quantity" data-price="180.00" value="0" min="0"></td>
                    <td class="price-cell">$180.00</td>
                </tr>
                <tr>
                    <td>Inmune cell</td>
                    <td><input type="number" class="product-quantity" data-price="190.00" value="0" min="0"></td>
                    <td class="price-cell">$190.00</td>
                </tr>
                <tr>
                    <td>Jarabe Natural</td>
                    <td><input type="number" class="product-quantity" data-price="190.00" value="0" min="0"></td>
                    <td class="price-cell">$190.00</td>
                </tr>
                <tr>
                    <td>Fortiman</td>
                    <td><input type="number" class="product-quantity" data-price="350.00" value="0" min="0"></td>
                    <td class="price-cell">$350.00</td>
                </tr>
                <tr>
                    <td>Gomelon</td>
                    <td><input type="number" class="product-quantity" data-price="150.00" value="0" min="0"></td>
                    <td class="price-cell">$150.00</td>
                </tr>
                <tr>
                    <td>Botella</td>
                    <td><input type="number" class="product-quantity" data-price="375.00" value="0" min="0"></td>
                    <td class="price-cell">$375.00</td>
                </tr>
                <tr>
                    <td>Botella Sana</td>
                    <td><input type="number" class="product-quantity" data-price="380.00" value="0" min="0"></td>
                    <td class="price-cell">$380.00</td>
                </tr>
                <tr>
                    <td>Fricion</td>
                    <td><input type="number" class="product-quantity" data-price="125.00" value="0" min="0"></td>
                    <td class="price-cell">$125.00</td>
                </tr>
                <tr>
                    <td>Fricilicom</td>
                    <td><input type="number" class="product-quantity" data-price="140.00" value="0" min="0"></td>
                    <td class="price-cell">$140.00</td>
                </tr>
                <tr>
                    <td>Mentol Ice bluc</td>
                    <td><input type="number" class="product-quantity" data-price="180.00" value="0" min="0"></td>
                    <td class="price-cell">$180.00</td>
                </tr>
                <tr>
                    <td>Grasa Cola de Caballo</td>
                    <td><input type="number" class="product-quantity" data-price="230.00" value="0" min="0"></td>
                    <td class="price-cell">$230.00</td>
                </tr>
                <tr>
                    <td>Grasa Madiel</td>
                    <td><input type="number" class="product-quantity" data-price="175.00" value="0" min="0"></td>
                    <td class="price-cell">$175.00</td>
                </tr>
                <tr>
                    <td>Borasol Liquido</td>
                    <td><input type="number" class="product-quantity" data-price="175.00" value="0" min="0"></td>
                    <td class="price-cell">$175.00</td>
                </tr>
                <tr>
                    <td>Borasol Polvo</td>
                    <td><input type="number" class="product-quantity" data-price="150.00" value="0" min="0"></td>
                    <td class="price-cell">$150.00</td>
                </tr>
                <tr>
                    <td>Baginol</td>
                    <td><input type="number" class="product-quantity" data-price="140.00" value="0" min="0"></td>
                    <td class="price-cell">$140.00</td>
                </tr>
                <tr>
                    <td>Calcio</td>
                    <td><input type="number" class="product-quantity" data-price="140.00" value="0" min="0"></td>
                    <td class="price-cell">$140.00</td>
                </tr>
                <tr>
                    <td>Cubeton</td>
                    <td><input type="number" class="product-quantity" data-price="230.00" value="0" min="0"></td>
                    <td class="price-cell">$230.00</td>
                </tr>
                <tr>
                    <td>ABC4</td>
                    <td><input type="number" class="product-quantity" data-price="240.00" value="0" min="0"></td>
                    <td class="price-cell">$240.00</td>
                </tr>
                <tr>
                    <td>R44</td>
                    <td><input type="number" class="product-quantity" data-price="230.00" value="0" min="0"></td>
                    <td class="price-cell">$230.00</td>
                </tr>
                <tr>
                    <td>Solongo</td>
                    <td><input type="number" class="product-quantity" data-price="150.00" value="0" min="0"></td>
                    <td class="price-cell">$150.00</td>
                </tr>
                <tr>
                    <td>Digestovo</td>
                    <td><input type="number" class="product-quantity" data-price="240.00" value="0" min="0"></td>
                    <td class="price-cell">$240.00</td>
                </tr>
                <tr>
                    <td>Prometo Pastilla</td>
                    <td><input type="number" class="product-quantity" data-price="370.00" value="0" min="0"></td>
                    <td class="price-cell">$370.00</td>
                </tr>
                <tr>
                    <td>Prometo Jarabe</td>
                    <td><input type="number" class="product-quantity" data-price="240.00" value="0" min="0"></td>
                    <td class="price-cell">$240.00</td>
                </tr>
                <tr>
                    <td>Acidil</td>
                    <td><input type="number" class="product-quantity" data-price="180.00" value="0" min="0"></td>
                    <td class="price-cell">$180.00</td>
                </tr>
                <tr>
                    <td>Cereforlte</td>
                    <td><input type="number" class="product-quantity" data-price="210.00" value="0" min="0"></td>
                    <td class="price-cell">$210.00</td>
                </tr>
                <tr>
                    <td>Complejo Jarabe</td>
                    <td><input type="number" class="product-quantity" data-price="140.00" value="0" min="0"></td>
                    <td class="price-cell">$140.00</td>
                </tr>
                <tr>
                    <td>Multivitaminico FOrmula 23</td>
                    <td><input type="number" class="product-quantity" data-price="325.00" value="0" min="0"></td>
                    <td class="price-cell">$325.00</td>
                </tr>
                <tr>
                    <td>Apecin</td>
                    <td><input type="number" class="product-quantity" data-price="180.00" value="0" min="0"></td>
                    <td class="price-cell">$180.00</td>
                </tr>
                <tr>
                    <td>Prolin</td>
                    <td><input type="number" class="product-quantity" data-price="225.00" value="0" min="0"></td>
                    <td class="price-cell">$225.00</td>
                </tr>
                <tr>
                    <td>Deparacitam</td>
                    <td><input type="number" class="product-quantity" data-price="140.00" value="0" min="0"></td>
                    <td class="price-cell">$140.00</td>
                </tr>
                <tr>
                    <td>Depuracu</td>
                    <td><input type="number" class="product-quantity" data-price="235.00" value="0" min="0"></td>
                    <td class="price-cell">$235.00</td>
                </tr>
                <tr>
                    <td>Cerebrina</td>
                    <td><input type="number" class="product-quantity" data-price="180.00" value="0" min="0"></td>
                    <td class="price-cell">$180.00</td>
                </tr>
                <tr>
                    <td>Gingo Biloba</td>
                    <td><input type="number" class="product-quantity" data-price="190.00" value="0" min="0"></td>
                    <td class="price-cell">$190.00</td>
                </tr>
                <tr>
                    <td>Bitamina E</td>
                    <td><input type="number" class="product-quantity" data-price="600.00" value="0" min="0"></td>
                    <td class="price-cell">$600.00</td>
                </tr>
                <tr>
                    <td>Omega 3</td>
                    <td><input type="number" class="product-quantity" data-price="340.00" value="0" min="0"></td>
                    <td class="price-cell">$340.00</td>
                </tr>
                <tr>
                    <td>Reuarim</td>
                    <td><input type="number" class="product-quantity" data-price="310.00" value="0" min="0"></td>
                    <td class="price-cell">$310.00</td>
                </tr>
                <tr>
                    <td>Sabila</td>
                    <td><input type="number" class="product-quantity" data-price="225.00" value="0" min="0"></td>
                    <td class="price-cell">$225.00</td>
                </tr>
                <tr>
                    <td>Estrato Vigorisante</td>
                    <td><input type="number" class="product-quantity" data-price="325.00" value="0" min="0"></td>
                    <td class="price-cell">$325.00</td>
                </tr>
                <tr>
                    <td>Estrato Vigorisante Pequeño</td>
                    <td><input type="number" class="product-quantity" data-price="185.00" value="0" min="0"></td>
                    <td class="price-cell">$185.00</td>
                </tr>
                <tr>
                    <td>Protana Jarabe</td>
                    <td><input type="number" class="product-quantity" data-price="550.00" value="0" min="0"></td>
                    <td class="price-cell">$550.00</td>
                </tr>
                <tr>
                    <td>Protana Pastilla</td>
                    <td><input type="number" class="product-quantity" data-price="700.00" value="0" min="0"></td>
                    <td class="price-cell">$700.00</td>
                </tr>
                <tr>
                    <td>Yobimen</td>
                    <td><input type="number" class="product-quantity" data-price="400.00" value="0" min="0"></td>
                    <td class="price-cell">$400.00</td>
                </tr>
                <tr>
                    <td>Power prins</td>
                    <td><input type="number" class="product-quantity" data-price="4700.00" value="0" min="0"></td>
                    <td class="price-cell">$4700.00</td>
                </tr>
                <tr>
                    <td>Siglo 22</td>
                    <td><input type="number" class="product-quantity" data-price="350.00" value="0" min="0"></td>
                    <td class="price-cell">$350.00</td>
                </tr>
                <tr>
                    <td>Colon</td>
                    <td><input type="number" class="product-quantity" data-price="500.00" value="0" min="0"></td>
                    <td class="price-cell">$500.00</td>
                </tr>
                <tr>
                    <td>Expecto plus</td>
                    <td><input type="number" class="product-quantity" data-price="175.00" value="0" min="0"></td>
                    <td class="price-cell">$175.00</td>
                </tr>
                <tr>
                    <td>Gecloven</td>
                    <td><input type="number" class="product-quantity" data-price="160.00" value="0" min="0"></td>
                    <td class="price-cell">$160.00</td>
                </tr>
                <tr>
                    <td>Vino sara</td>
                    <td><input type="number" class="product-quantity" data-price="350.00" value="0" min="0"></td>
                    <td class="price-cell">$350.00</td>
                </tr>
                <tr>
                    <td>Geinore</td>
                    <td><input type="number" class="product-quantity" data-price="225.00" value="0" min="0"></td>
                    <td class="price-cell">$225.00</td>
                </tr>
                <tr>
                    <td>Combel</td>
                    <td><input type="number" class="product-quantity" data-price="210.00" value="0" min="0"></td>
                    <td class="price-cell">$210.00</td>
                </tr>
                <tr>
                    <td>Chanpu Cola de Caballo</td>
                    <td><input type="number" class="product-quantity" data-price="140.00" value="0" min="0"></td>
                    <td class="price-cell">$140.00</td>
                </tr>
                <tr>
                    <td>Tratamiento Cola de Caballo</td>
                    <td><input type="number" class="product-quantity" data-price="190.00" value="0" min="0"></td>
                    <td class="price-cell">$190.00</td>
                </tr>
                <tr>
                    <td>Colageno</td>
                    <td><input type="number" class="product-quantity" data-price="550.00" value="0" min="0"></td>
                    <td class="price-cell">$550.00</td>
                </tr>
                <tr>
                    <td>citracto de Macnecio</td>
                    <td><input type="number" class="product-quantity" data-price="550.00" value="0" min="0"></td>
                    <td class="price-cell">$550.00</td>
                </tr>
                <tr>
                    <td>Compuesto Celia</td>
                    <td><input type="number" class="product-quantity" data-price="300.00" value="0" min="0"></td>
                    <td class="price-cell">$300.00</td>
                </tr>
                <tr>
                    <td>Pomada Collado</td>
                    <td><input type="number" class="product-quantity" data-price="225.00" value="0" min="0"></td>
                    <td class="price-cell">$225.00</td>
                </tr>
                <tr>
                    <td>Fosfo B-12</td>
                    <td><input type="number" class="product-quantity" data-price="550.00" value="0" min="0"></td>
                    <td class="price-cell">$550.00</td>
                </tr>
            </tbody>
        </table>
    </div>
    <script>
        // Obtener el campo de búsqueda y la tabla
        const searchInput = document.getElementById('searchInput');
        const productsTable = document.getElementById('productsTable');
        const rows = productsTable.getElementsByTagName('tr');

        // Escuchar el evento 'keyup' en el campo de búsqueda
        searchInput.addEventListener('keyup', function() {
            const filter = searchInput.value.toLowerCase();
            for (let i = 1; i < rows.length; i++) {
                const row = rows[i];
                // El índice de la columna del producto es 0
                const productName = row.getElementsByTagName('td')[0].textContent.toLowerCase();

                if (productName.includes(filter)) {
                    row.style.display = '';
                } else {
                    row.style.display = 'none';
                }
            }
        });

        // --- Código para la suma de productos por cantidad ---
        const quantityInputs = document.querySelectorAll('.product-quantity');
        const totalPriceElement = document.getElementById('totalPrice');

        function calculateTotal() {
            let total = 0;
            quantityInputs.forEach(input => {
                const price = parseFloat(input.dataset.price);
                const quantity = parseInt(input.value);

                if (!isNaN(quantity) && quantity > 0) {
                    total += price * quantity;
                }
            });

            totalPriceElement.textContent = `$${total.toFixed(2)}`;
        }

        quantityInputs.forEach(input => {
            input.addEventListener('change', calculateTotal);
            input.addEventListener('input', calculateTotal);
        });

        calculateTotal();
    </script>
</body>
</html>
