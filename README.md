
esto es solo la primera pagina la raiz de la pagina web en mi .rar encontraras las demas paginas
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inventario de Ventas de Computadoras</title>
    <link rel="stylesheet" href="computadora.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600&family=Playfair+Display:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Montserrat', sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            min-height: 100vh;
            margin: 0;
            background-color: #f4f4f4;
            color: #333;
            text-align: center; /* Centra el texto en el body */
        }
        header {
            background-color: #34495e;
            color: white;
            padding: 30px 0;
            margin-bottom: 30px;
            width: 100%;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        header h1 {
            font-family: 'Playfair Display', serif;
            font-size: 2.5em;
            margin-bottom: 10px;
        }
        .menu {
            margin-top: 20px;
        }
        .menu label {
            margin-right: 10px;
            font-weight: 600;
        }
        .menu select {
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }
        #lista-precios {
            display: none;
            margin-top: 20px;
            padding: 20px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        #lista-precios div {
            border-bottom: 1px solid #eee;
            padding-bottom: 15px;
            margin-bottom: 15px;
        }
        #lista-precios div:last-child {
            border-bottom: none;
        }
        #lista-precios h3 {
            font-family: 'Playfair Display', serif;
            margin-top: 0;
            color: #555;
        }
        #imagenes-productos {
            display: none;
        }
        .imagen-producto {
            width: 100px;
            margin: 10px;
            border-radius: 5px;
            box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
        }
        main {
            width: 80%; /* O ajusta el ancho según sea necesario */
            max-width: 900px; /* Limita el ancho máximo */
            padding: 20px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        #inventario {
            margin-bottom: 30px;
            text-align: left;
        }
        #inventario h2 {
            font-family: 'Playfair Display', serif;
            font-size: 2em;
            margin-bottom: 15px;
            color: #444;
            text-align: center;
        }
        #inventario ul {
            list-style: none;
            padding: 0;
        }
        #inventario li {
            padding: 8px 0;
            border-bottom: 1px solid #eee;
        }
        #inventario li:last-child {
            border-bottom: none;
        }
        .auth-buttons {
            position: absolute;
            top: 10px;
            right: 10px;
        }
        .auth-buttons button {
            margin-left: 10px;
            padding: 10px 15px;
            border: none;
            border-radius: 5px;
            background-color: #5cb85c;
            color: white;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        .auth-buttons button:hover {
            background-color: #4cae4c;
        }
        #mostrar-precios, #mostrar-pago {
            padding: 12px 20px;
            border: none;
            border-radius: 5px;
            background-color: #007bff;
            color: white;
            cursor: pointer;
            font-size: 1em;
            margin: 10px 5px;
            transition: background-color 0.3s ease;
        }
        #mostrar-precios:hover, #mostrar-pago:hover {
            background-color: #0056b3;
        }
        .stock-badge {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.8em;
            font-weight: bold;
            margin-left: 10px;
        }
        .stock-available {
            background-color: #d4edda;
            color: #155724;
        }
        .stock-low {
            background-color: #fff3cd;
            color: #85640a;
        }
        .stock-out {
            background-color: #f8d7da;
            color: #721c24;
        }
    </style>
</head>
<body>
    <div class="auth-buttons">
        <button onclick="window.location.href='pagina de registro cliente.html'">Registro</button>
        <button onclick="window.location.href='verificacion de registro.html'">Bienvenida</button>
    </div>
    <header>
        <h1>Inventario de Ventas de Computadoras</h1>
        <div class="menu">
            <label for="categoria">Categoría:</label>
            <select id="categoria">
                <option value="todos">Todos</option>
            </select>

            <label for="precio">Precio:</label>
            <select id="precio">
                <option value="todos">Todos</option>
                <option value="bajo">Bajo</option>
                <option value="medio">Medio</option>
                <option value="alto">Alto</option>
            </select>
        </div>
    </header>

    <main>
        <div id="inventario">
            <h2>Accesorios Disponibles</h2>
            <ul id="lista-productos-accesorios">
                </ul>
        </div>

        <div id="inventario">
            <h2>Productos Disponibles</h2>
            <ul id="lista-productos-computadoras">
                </ul>
        </div>

        <button id="mostrar-precios">Mostrar Precios</button>
        <button id="mostrar-pago">Método de Pago</button>

        <div id="lista-precios">
            </div>
    </main>

    <script>
        const productos = [
            { nombre: 'Mouse', precio: 20, categoria: 'accesorios', imagen: 'https://i.pinimg.com/736x/eb/82/2d/eb822d169f4443b8ea49386456299ae8.jpg', stock: 10 },
            { nombre: 'Audífonos', precio: 30, categoria: 'accesorios', imagen: 'audifonos.jpg', stock: 5 },
            { nombre: 'Micrófono', precio: 25, categoria: 'accesorios', imagen: 'microfono.jpg', stock: 0 },
            { nombre: 'Teclado', precio: 15, categoria: 'accesorios', imagen: 'teclado.jpg', stock: 15 },
            { nombre: 'Monitores', precio: 100, categoria: 'accesorios', imagen: '', stock: 3 },
            { nombre: 'Computadora 4ta', precio: 80, categoria: 'desktop', imagen: '', stock: 2 },
            { nombre: 'Computadora 5ta', precio: 150, categoria: 'desktop', imagen: 'computadora5ta.jpg', stock: 7 },
            { nombre: 'Computadora 6ta', precio: 150, categoria: 'desktop', imagen: 'computadora6ta.jpg', stock: 0 },
            { nombre: 'Computadora 7ma', precio: 300, categoria: 'desktop', imagen: 'computadora7ma.jpg', stock: 4 },
            { nombre: 'Computadora 9na', precio: 600, categoria: 'desktop', imagen: 'computadora9na.jpg', stock: 1 },
        ];

        const listaPreciosDiv = document.getElementById('lista-precios');
        const mostrarPreciosBtn = document.getElementById('mostrar-precios');
        const mostrarPagoBtn = document.getElementById('mostrar-pago');
        const listaProductosAccesoriosUl = document.getElementById('lista-productos-accesorios');
        const listaProductosComputadorasUl = document.getElementById('lista-productos-computadoras');

        function actualizarInventario() {
            listaProductosAccesoriosUl.innerHTML = '';
            listaProductosComputadorasUl.innerHTML = '';

            productos.forEach(producto => {
                const listItem = document.createElement('li');
                listItem.textContent = producto.nombre;
                const stockBadge = document.createElement('span');
                stockBadge.classList.add('stock-badge');
                if (producto.stock > 5) {
                    stockBadge.classList.add('stock-available');
                    stockBadge.textContent = `disponible: ${producto.stock}`;
                } else if (producto.stock > 0) {
                    stockBadge.classList.add('stock-low');
                     stockBadge.textContent = `poca mercancia: ${producto.stock}`;
                } else {
                    stockBadge.classList.add('stock-out');
                    stockBadge.textContent = 'Agotado';
                }
                listItem.appendChild(stockBadge);

                if (producto.categoria === 'accesorios') {
                    listaProductosAccesoriosUl.appendChild(listItem);
                } else if (producto.categoria === 'desktop') {
                    listaProductosComputadorasUl.appendChild(listItem);
                }
            });
        }

        actualizarInventario(); // Llama a la función para mostrar el inventario inicial

        mostrarPreciosBtn.addEventListener('click', function() {
            listaPreciosDiv.innerHTML = ''; // Limpia el contenido anterior
            productos.forEach(producto => {
                const productoDiv = document.createElement('div');
                productoDiv.innerHTML = `
                    <h3>${producto.nombre} - $${producto.precio}</h3>
                    ${producto.imagen ? `<img src="${producto.imagen}" alt="${producto.nombre}" class="imagen-producto">` : ''}
                    <p>Stock: ${producto.stock}</p>
                `;
                listaPreciosDiv.appendChild(productoDiv);
            });
            listaPreciosDiv.style.display = 'block';
        });

        mostrarPagoBtn.addEventListener('click', function() {
            window.location.href = 'pago.html'; // Redirige a la página de pago
        });
    </script>
</body>
</html>
