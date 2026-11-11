# APEX DRIVE - Professional Car Rental System (Project 7)

A state-of-the-art, 8-page luxury and heavy vehicle car rental web application with modern glassmorphism aesthetics, responsive layouts, client-side relational database persistence (`localStorage`), date-range collision avoidance engine, staff pickup/return workflows, and live execution of all 8 required project queries.

---

## 🌟 Overview & Key Features

- **8 Dedicated Website Pages (Surfaces)**: Exactly matches the specifications of **Project 7: Car Rental System**.
- **Heavy & Luxury Vehicles Fleet**: Specially populated with heavy SUVs and 4x4 vehicles (Toyota Land Cruiser 300 ZX, Mercedes G63 AMG G-Wagon, Land Rover Defender 110, Cadillac Escalade Platinum, Range Rover Autobiography, Toyota Hilux Revo Rocco, Lamborghini Urus, Porsche 911, and Executive Sedans).
- **Zero-Dependency Architecture**: Runs in any modern browser (Chrome, Edge, Firefox) simply by opening `index.html`. No Node.js or Python backend server required.
- **Persistent Relational Database**: Implements all 5 database tables with full relational references and data persistence across reloads.
- **Strict Business Rules Enforcement**:
  1. **No Overlapping Bookings**: Automatically checks `(new_start <= existing_end) AND (new_end >= existing_start)`.
  2. **Maintenance Locking**: Vehicles under maintenance cannot be booked.
  3. **Tariff Calculation**: `Amount = days * daily_rate`.
  4. **Date Integrity**: `end_date >= start_date`.

---

## 📑 The 8 Project Pages (Surfaces)

| # | Page File | Purpose & Features | User Persona |
|---|---|---|---|
| **1** | [`index.html`](file:///c:/Users/zulqa/OneDrive/Desktop/New%20folder/index.html) | **Search Available Cars by Date Range & Type**<br>Live date range picker, category filter (Heavy 4x4, Sedan, Hatchback, Sports), overlap validation, available fleet cards with instant "Rent Car" CTAs. | Customer |
| **2** | [`car-details.html`](file:///c:/Users/zulqa/OneDrive/Desktop/New%20folder/car-details.html) | **Car Details**<br>High-resolution vehicle gallery, full technical specs (Engine, HP, Drivetrain, Seats, Transmission), rental policies, and real-time daily rate estimator. | Customer |
| **3** | [`booking.html`](file:///c:/Users/zulqa/OneDrive/Desktop/New%20folder/booking.html) | **Booking Form**<br>Step-by-step reservation wizard, conflict detection alerts, customer CNIC & License capture, payment method selector (Cash, Card, Online), and instant invoice calculation. | Customer |
| **4** | [`my-bookings.html`](file:///c:/Users/zulqa/OneDrive/Desktop/New%20folder/my-bookings.html) | **My Bookings & Invoices**<br>Filter by status (Active, Upcoming, Completed, Cancelled), cancellation release, and printable official rental voucher / invoice with signatures. | Customer |
| **5** | [`pickup-return.html`](file:///c:/Users/zulqa/OneDrive/Desktop/New%20folder/pickup-return.html) | **Staff: Pickup and Return Screen**<br>Handover screen (record pickup odometer & checklist, set car to 'Rented') + Return screen (record return odometer, compute driven KM, adjust extra charges, collect payment, set car to 'Available'). | Staff / Admin |
| **6** | [`add-car.html`](file:///c:/Users/zulqa/OneDrive/Desktop/New%20folder/add-car.html) | **Add Car (Fleet Management)**<br>Register new vehicles with unique registration plate validation, preset autofill buttons (LC300, G-Wagon, Defender), and real-time card preview. | Staff / Admin |
| **7** | [`maintenance.html`](file:///c:/Users/zulqa/OneDrive/Desktop/New%20folder/maintenance.html) | **Maintenance Status**<br>Fleet health monitoring, workshop job scheduling, toggle status between 'Available' and 'Maintenance', and live proof of booking locking rule. | Staff / Admin |
| **8** | [`revenue-report.html`](file:///c:/Users/zulqa/OneDrive/Desktop/New%20folder/revenue-report.html) | **Revenue Report & Analytics**<br>Chart.js visualizations + live interactive execution of all 8 required project queries + CSV export + concurrency control documentation. | Staff / Admin |

---

## 🗄️ Relational Database Schema (5 Tables)

1. **`Car_Types`**:
   - `type_id (PK)`
   - `type_name` ('Heavy 4x4 / Luxury SUV', 'Executive Sedan', 'Premium Hatchback', 'Exotic & Sports')
   - `daily_rate`

2. **`Cars`**:
   - `car_id (PK)`
   - `type_id (FK)`
   - `reg_no (UNIQUE)` (e.g. `ISB-LC-300`, `LHR-GW-063`)
   - `model` (e.g. Toyota Land Cruiser 300 ZX)
   - `year`
   - `status` (`'Available'`, `'Rented'`, `'Maintenance'`)

3. **`Customers`**:
   - `customer_id (PK)`
   - `name`
   - `cnic (UNIQUE)` (e.g. `37405-1234567-1`)
   - `license_no (UNIQUE)` (e.g. `PK-ISB-9921`)
   - `phone`

4. **`Bookings`**:
   - `booking_id (PK)`
   - `car_id (FK)`
   - `customer_id (FK)`
   - `start_date`
   - `end_date`
   - `status` (`'Confirmed'`, `'Active'`, `'Completed'`, `'Cancelled'`)
   - `pickup_mileage`, `return_mileage`, `total_days`, `total_amount`

5. **`Payments`**:
   - `payment_id (PK)`
   - `booking_id (FK)`
   - `amount`
   - `method` (`'Cash'`, `'Card'`, `'Online'`)
   - `paid_on`

---

## 📊 Live Execution of the 8 Required Queries

On **Page 8 (`revenue-report.html`)**, all 8 queries are executed against the live dataset:
1. **Query 1:** Cars available between two dates (`NOT EXISTS` overlap condition).
2. **Query 2:** Revenue per car type per month (interactive Chart.js bar & doughnut charts).
3. **Query 3:** Most rented car model.
4. **Query 4:** Customers with unpaid bookings.
5. **Query 5:** Average rental duration.
6. **Query 6:** Cars never rented.
7. **Query 7:** Bookings that overlap (system audit test verifying 0 invalid overlaps).
8. **Query 8:** Top 3 customers by total spend.

---

## 🚀 How to Run the Website

1. Navigate to the folder:
   `c:\Users\zulqa\OneDrive\Desktop\New folder`
2. Double-click **`index.html`** to launch in Google Chrome or any browser.
3. Use the top navigation bar to seamlessly move across all 8 surfaces or switch between **Customer Mode** and **Staff / Admin Mode**.
4. To test data reset, click **"Reset DB"** in the top navigation or footer at any time.
