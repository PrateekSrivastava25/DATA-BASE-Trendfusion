-- Database creation
CREATE DATABASE ecommerce_website;

-- Use the created database
USE ecommerce_website;

-- Table for products
CREATE TABLE products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(255) NOT NULL,
    product_description TEXT,
    price DECIMAL(10, 2) NOT NULL,
    quantity_available INT NOT NULL,
    image_url VARCHAR(255) -- Link to the product image
);

-- Table for users (buyers and sellers)
CREATE TABLE users (
    user_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    phone VARCHAR(15) NOT NULL,
    user_type ENUM('buyer', 'seller') NOT NULL
);

-- Table for orders
CREATE TABLE orders (
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    buyer_id INT NOT NULL,
    product_id INT NOT NULL,
    quantity INT NOT NULL,
    order_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (buyer_id) REFERENCES users(user_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);

-- Table for WhatsApp messages (optional, for tracking purposes)
CREATE TABLE messages (
    message_id INT AUTO_INCREMENT PRIMARY KEY,
    buyer_id INT NOT NULL,
    seller_id INT NOT NULL,
    product_id INT NOT NULL,
    message_text TEXT,
    message_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (buyer_id) REFERENCES users(user_id),
    FOREIGN KEY (seller_id) REFERENCES users(user_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);

-- Insert sample data into products
INSERT INTO products (product_name, product_description, price, quantity_available, image_url)
VALUES 
('Laptop', 'A high-performance laptop with 16GB RAM and 512GB SSD.', 75000.00, 10, 'images/laptop.jpg'),
('Smartphone', 'Latest Android smartphone with 8GB RAM.', 30000.00, 20, 'images/smartphone.jpg'),
('Headphones', 'Noise-canceling over-ear headphones.', 5000.00, 50, 'images/headphones.jpg');

-- Insert sample data into users
INSERT INTO users (name, email, phone, user_type)
VALUES
('John Doe', 'john@example.com', '1234567890', 'buyer'),
('Jane Smith', 'jane@example.com', '0987654321', 'seller');

-- Insert sample data into orders
INSERT INTO orders (buyer_id, product_id, quantity)
VALUES
(1, 1, 2),  -- John Doe orders 2 laptops
(1, 3, 1);  -- John Doe orders 1 headphone

-- Insert sample data into messages
INSERT INTO messages (buyer_id, seller_id, product_id, message_text)
VALUES
(1, 2, 1, 'I want to buy 2 laptops. Can you confirm the availability?');
