User Table
CREATE TABLE User (
    user_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    phone_number VARCHAR(20)
);

Address Table
CREATE TABLE Address (
    address_id INT AUTO_INCREMENT PRIMARY KEY,
    street VARCHAR(255),
    city VARCHAR(100),
    state VARCHAR(100),
    country VARCHAR(100),
    postal_code VARCHAR(20)
);

Property Table
CREATE TABLE Property (
    property_id INT AUTO_INCREMENT PRIMARY KEY,
    owner_id INT NOT NULL,
    title VARCHAR(255),
    description TEXT,
    address_id INT,
    price DECIMAL(10, 2),
    FOREIGN KEY (owner_id) REFERENCES User(user_id),
    FOREIGN KEY (address_id) REFERENCES Address(address_id)
);

Review Table
CREATE TABLE Review (
    review_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    property_id INT NOT NULL,
    rating INT CHECK (rating BETWEEN 1 AND 5),
    comment TEXT,
    review_date DATE,
    FOREIGN KEY (user_id) REFERENCES User(user_id),
    FOREIGN KEY (property_id) REFERENCES Property(property_id)
);

Payment Table
CREATE TABLE Payment (
    payment_id INT AUTO_INCREMENT PRIMARY KEY,
    booking_id INT, -- assuming a bookings table exists
    amount DECIMAL(10, 2) NOT NULL,
    payment_method VARCHAR(50),
    payment_date DATE,
    status VARCHAR(50),
    FOREIGN KEY (booking_id) REFERENCES Booking(booking_id)
);

Message Table
CREATE TABLE Message (
    message_id INT AUTO_INCREMENT PRIMARY KEY,
    sender_id INT NOT NULL,
    receiver_id INT NOT NULL,
    message TEXT,
    sent_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (sender_id) REFERENCES User(user_id),
    FOREIGN KEY (receiver_id) REFERENCES User(user_id)
);
