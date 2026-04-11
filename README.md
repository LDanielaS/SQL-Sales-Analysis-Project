# Proyecto 1 -Análisis de datos

- “codigo que crea nuevo id del 1- en adelante para agregar los datos (no usado)
    
    ```sql
    INSERT INTO Customers (Id_Customer, Name_Customer, City_Customer)
    SELECT 
        ROW_NUMBER() OVER () AS Id_Customer,
        `Customer Name`,
        City
    FROM (
        SELECT DISTINCT `Customer Name`, City
        FROM sample__superstore
    ) AS unique_customers;
    ```
    

- Esto es para ajustar que siempre la lectura de datos sea asi con . y no ,:
    
    ```sql
    LOAD DATA INFILE 'archivo.csv'
    INTO TABLE tu_tabla
    FIELDS TERMINATED BY ','
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS
    (@columna)
    SET tu_columna = REPLACE(@columna, ',', '.');
    ```
    

**Proyecto: Análisis de ventas con SQL**

- Modelado de base de datos relacional
- Análisis de ventas, clientes y productos
- Identificación de tendencias y métricas clave
- Uso de JOIN, GROUP BY y funciones ventana (LAG)

Creación y modificación de tablas:

```sql
CREATE TABLE Customers(
    Id_Customer int,
    Name_Customer varchar(100),
    City_Customer varchar(50));
    
CREATE TABLE Products(
    Id_Product int,
    Name_Product varchar(100),
    Category_Product varchar(100),
    Price_Product decimal(19, 4));
    
CREATE TABLE Sales(
    Id_Sale int,
    Id_Customer int,
    Id_Product int,
    Date_Sale date,
    Quantity_Sold int);
    
ALTER TABLE Customers
MODIFY Id_Customer char(8);

ALTER TABLE Products
MODIFY Id_Product varchar(20);

ALTER TABLE Sales
MODIFY Id_Sale varchar(20);

ALTER TABLE Products
MODIFY Name_Product varchar();
```

Para insertar los datos de id,nombre y ciudad de cliente desde la tabla sample_cvs hasta la tabla Customers:

```sql
INSERT INTO Customers (Id_Customer, Name_Customer, City_Customer) #tabla nuestra
SELECT DISTINCT 
    `Customer ID`, #tabla de origen
    `Customer Name`,
    City
FROM sample_cvs; 
```

```sql
INSERT INTO Products (Id_Product, Name_Product, Category_Product) #tabla nuestra
SELECT DISTINCT 
    `Product ID`, #tabla de origen
    `Product Name`,
    Category
FROM sample_cvs; 
```

```sql
INSERT INTO Sales (
    Id_Sale, Id_Customer, Id_Product, Date_Sale, Quantity_Sold, Unit_Price, Discount, Profit, Sales_T
)
SELECT
    `Order ID`,
    `Customer ID`,
    `Product ID`,
    STR_TO_DATE(`Order Date`, '%m/%d/%Y'),
    Quantity,
    Sales / Quantity AS Unit_Price,
    Discount,
    Profit,
    Sales
FROM sample_cvs;INSERT INTO Sales (
    Id_Sale, Id_Customer, Id_Product, Date_Sale, Quantity_Sold, Unit_Price, Discount, Profit, Sales_T
)
SELECT
    `Order ID`,
    `Customer ID`,
    `Product ID`,
    STR_TO_DATE(`Order Date`, '%m/%d/%Y'),
    Quantity,
    Sales / Quantity AS Unit_Price,
    Discount,
    Profit,
    Sales
FROM sample_cvs;
```

Para la tabla Sales, primero se modifico agregando nuevas columnas:

```sql
ALTER TABLE Sales
ADD Discount decimal(10,5); 
```

```sql
ALTER TABLE Sales
MODIFY Id_Customer CHAR(8),
MODIFY Id_Product VARCHAR(20);
```

Luego se cambio , por puntos

```sql
UPDATE sample_cvs
SET Discount = REPLACE(Discount, ',', '.');

UPDATE sample_cvs
SET Sales = REPLACE(Sales, ',', '.');

UPDATE sample_cvs
SET Profit = REPLACE(Profit, ',', '.');
```

Y se cambio formato de origen y de llegada a numeros

```sql
ALTER TABLE sample_cvs
MODIFY Discount decimal(10,5);
```

Para las fechas, primero se creo una nueva columna, luego se extraen los datos de la columna original para imprimir en el orden general del SQL (Año/Mes/Dia)

```sql
ALTER TABLE sample_cvs 
ADD order_date_new DATE;

UPDATE sample_cvs
SET order_date_new = STR_TO_DATE(`Order Date`, '%m/%d/%Y');
```

### Analisis de datos en practica

Para analizar los datos obtenidos en cada tabla, primero se obtiene:

- Ventas totales de la empresa:
    
    ```sql
    SELECT SUM(Sales_T) AS Total_Sales
    FROM Sales;
    ```
    
    ![image.png](Proyecto%201%20-An%C3%A1lisis%20de%20datos/image.png)
    
- Productos organizados con el que tiene mas ventas:
    
    (El s y p son “alias” de las tablas Sales y Products que son designadas en FROM Sales s y JOIN products p, luego toma el nombre de p y la cantidad de ventas de s, luego UNE ambas tablas con JOIN donde la condicion ON se cumpla, es decir donde los Id de la tabla s sean iguales a los Id de la p, luego lo agrupa por nombres y por ultimo los ordena de forma descendente) 
    
    ```sql
    SELECT 
        p.Name_Product,
        SUM(s.Quantity_Sold) AS Total_Sales_Product
    FROM Sales s
    JOIN Products p ON s.Id_Product = p.Id_Product
    GROUP BY p.Name_Product
    ORDER BY Total_Sales_Product DESC;
    ```
    
    ![image.png](Proyecto%201%20-An%C3%A1lisis%20de%20datos/image%201.png)
    
- Ventas por ciudad
    
    ```sql
    SELECT 
        c.City_Customer,
        SUM(s.Sales_T) AS Total_Sales
    FROM Sales s
    JOIN Customers c ON s.Id_Customer = c.Id_Customer
    GROUP BY c.City_Customer
    ORDER BY Total_Sales DESC;
    ```
    
    ![image.png](Proyecto%201%20-An%C3%A1lisis%20de%20datos/image%202.png)
    
- Mejores clientes
    
    ```sql
    SELECT 
        c.Name_Customer,
        SUM(s.Sales_T) AS Total_Purchased
    FROM Sales s
    JOIN Customers c ON s.Id_Customer = c.Id_Customer
    GROUP BY c.Name_Customer
    ORDER BY Total_Purchased DESC;
    ```
    
    ![image.png](Proyecto%201%20-An%C3%A1lisis%20de%20datos/image%203.png)
    
- Valor promedio de ticket de venta
    
    ```sql
    SELECT 
        AVG(Sales_T) AS Average_Ticket
    FROM Sales;
    ```
    
    ![image.png](Proyecto%201%20-An%C3%A1lisis%20de%20datos/image%204.png)
    
- Crecimiento mensual de la empresa
    
    ```sql
    SELECT 
        DATE_FORMAT(Date_Sale, '%Y-%m') AS Month,
        SUM(Sales_T) AS Sales_Month,
        LAG(SUM(Sales_T)) OVER (ORDER BY DATE_FORMAT(Date_Sale, '%Y-%m')) AS Previous_month
    FROM Sales
    GROUP BY Month;
    ```
    
    ![image.png](Proyecto%201%20-An%C3%A1lisis%20de%20datos/image%205.png)
