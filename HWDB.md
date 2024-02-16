CREATE TABLE kategori_barang
(
	id_kategori SERIAL PRIMARY KEY,
	nama_kategori VARCHAR(255)
);

CREATE TABLE barang (
  id_barang SERIAL PRIMARY KEY,
  nama_barang VARCHAR(255),
  harga DECIMAL(10, 2),
  stok INT,
  id_kategori INT,
  FOREIGN KEY (id_kategori) REFERENCES kategori_barang(id_kategori)
);

-- Select semua data barang
SELECT FROM barang;

INSERT INTO barang(id_barang, nama_barang, harga, stok)
VALUES(1, 'Mainan Mobil', 150000, 100);

UPDATE barang SET harga = 200000, stok = 15 WHERE id_barang = 1;

-- Select semua data kategori barang
SELECT FROM kategori_barang;

INSERT INTO kategori_barang (nama_kategori)
VALUES ('Mainan Anak-Anak');

UPDATE kategori_barang SET nama_kategori = 'Mainan Balita' WHERE id_kategori = 1;

-- Select data barang dan nama kategori barang

SELECT barang.nama_barang, barang.harga, kategori_barang.nama_kategori
FROM barang
JOIN kategori_barang ON barang.id_kategori = kategori_barang.id_kategori;
