# E-Commerce-
Mini E-Commerce React Project. A Single-Page React project showcasing real product images, interactive product details, and a clean, responsive design. Built to demonstrate Front-End development skills using React, JSX, and modern JavaScript. Features include product cards with images, titles, prices, and descriptions, interactive 

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Mini E-Commerce</title>
  <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  <style>
    body { font-family: Arial, sans-serif; margin:0; padding:0; background:#f9f9f9; }
    button { cursor:pointer; padding:0.5rem 1rem; margin:5px; border:none; background:#0d6efd; color:white; border-radius:4px; }
    nav { display:flex; justify-content:space-between; background:#0d6efd; color:white; padding:1rem; }
    footer { text-align:center; padding:1rem; background:#f1f1f1; margin-top:2rem; }
    .container { padding:1rem; }
    .product-card { border:1px solid #ddd; padding:1rem; text-align:center; margin-bottom:1rem; background:white; border-radius:5px; box-shadow:0 0 5px rgba(0,0,0,0.1); }
    .product-card img { max-width:150px; height:auto; margin-bottom:0.5rem; }
    .product-details { background:white; padding:1rem; border-radius:5px; box-shadow:0 0 10px rgba(0,0,0,0.1); max-width:500px; margin:1rem auto; text-align:center; }
    .product-details img { max-width:300px; height:auto; display:block; margin:0 auto 1rem; }
    h1,h2,h3,p { margin:5px 0; }
  </style>
</head>
<body>
  <div id="root"></div>
  <script type="text/babel">
    const { useState } = React;

    const products = [
      {
        id: 1,
        title: "Wireless Headphones",
        price: 120,
        image: "https://images.pexels.com/photos/373945/pexels-photo-373945.jpeg",
        description: "High-quality wireless headphones with comfortable design and excellent sound."
      },
      {
        id: 2,
        title: "Smart Watch",
        price: 199,
        image: "https://images.pexels.com/photos/277421/pexels-photo-277421.jpeg",
        description: "Feature-packed smart watch with health tracking and sleek modern design."
      },
      {
        id: 3,
        title: "Portable Bluetooth Speaker",
        price: 80,
        image: "https://images.pexels.com/photos/63703/pexels-photo-63703.jpeg",
        description: "Compact and powerful Bluetooth speaker perfect for parties and outdoor use."
      }
    ];

    const Navbar = ({ setPage }) => (
      <nav>
        <h1>Mini Store</h1>
        <div>
          <button onClick={() => setPage("home")}>Home</button>
          <button onClick={() => setPage("about")}>About</button>
        </div>
      </nav>
    );

    const Footer = () => <footer>© 2026 Mini Store</footer>;

    const ProductCard = ({ product, setPage, setSelected }) => (
      <div className="product-card">
        <img src={product.image} alt={product.title} />
        <h3>{product.title}</h3>
        <p>${product.price}</p>
        <button onClick={() => { setSelected(product); setPage("details"); }}>View Details</button>
      </div>
    );

    const Home = ({ setPage, setSelected }) => (
      <div className="container">
        <h2>Products</h2>
        {products.map(p => (
          <ProductCard key={p.id} product={p} setPage={setPage} setSelected={setSelected} />
        ))}
      </div>
    );

    const ProductDetails = ({ product, setPage }) => (
      <div className="container product-details">
        <img src={product.image} alt={product.title} />
        <h2>{product.title}</h2>
        <h3>${product.price}</h3>
        <p>{product.description}</p>
        <button onClick={() => setPage("home")}>Back to Home</button>
      </div>
    );

    const About = () => (
      <div className="container">
        <h2>About Mini Store</h2>
        <p>This is a Single-File React Mini E-Commerce project built for learning and portfolio showcase, featuring real product images and descriptive details.</p>
      </div>
    );

    const App = () => {
      const [page, setPage] = useState("home");
      const [selected, setSelected] = useState(null);

      return (
        <div>
          <Navbar setPage={setPage} />
          {page === "home" && <Home setPage={setPage} setSelected={setSelected} />}
          {page === "details" && selected && <ProductDetails product={selected} setPage={setPage} />}
          {page === "about" && <About />}
          <Footer />
        </div>
      );
    };

    ReactDOM.createRoot(document.getElementById("root")).render(<App />);
  </script>
</body>
</html>
