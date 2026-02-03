# My Salon - Appointment Booking System

A command-line based salon appointment booking system built with Bash and PostgreSQL. This project allows customers to book salon services, manage customer information, and track appointments.

## 📁 Project Structure

```
my-salon/
├── salon.sh          # Main Bash script for the salon booking system
├── salon.sql         # Database schema and initial data
└── README.md         # This file
```

## 🚀 Features

- **Interactive Menu System**: Easy-to-navigate CLI interface for customers
- **Service Selection**: Choose from available salon services (Wig install, Fade Cut, Hair Wash)
- **Customer Management**: 
  - New customer registration
  - Existing customer recognition by phone number
- **Appointment Booking**: Schedule appointments with time selection
- **Input Validation**: Robust error handling for invalid inputs
- **Database Persistence**: All data stored in PostgreSQL database

## 🛠️ Technologies Used

- **Bash Scripting** - Interactive command-line interface
- **PostgreSQL** - Relational database for data storage
- **PSQL Command Line** - Database interaction

## 🗄️ Database Schema

### Tables

#### `services`
- `service_id` (PK) - Unique service identifier
- `name` - Service name

#### `customers`
- `customer_id` (PK) - Unique customer identifier
- `phone` (UNIQUE) - Customer phone number
- `name` - Customer name

#### `appointments`
- `appointment_id` (PK) - Unique appointment identifier
- `customer_id` (FK) - References customers table
- `service_id` (FK) - References services table
- `time` - Appointment time
- `name` - [Note: This column appears redundant in the schema]

### Preloaded Services
1. Wig install
2. Fade Cut
3. Hair Wash

## 📋 Prerequisites

Before running this application, ensure you have:

- **PostgreSQL** installed and running
- **Bash shell** (available on Linux, macOS, or Windows WSL)
- Appropriate permissions to create databases and tables

## ⚙️ Installation & Setup

### 1. Set up the Database

```bash
# Create and populate the database
psql -U postgres -f salon.sql
```

Alternatively, you can run the SQL commands directly in psql.

### 2. Configure Database Connection

The script uses the following connection parameters:
- Username: `freecodecamp`
- Database: `salon`

Make sure the `freecodecamp` user exists and has appropriate permissions:
```bash
# Create user if needed
sudo -u postgres createuser --superuser freecodecamp
```

### 3. Make the Script Executable

```bash
chmod +x salon.sh
```

## 🎮 How to Use

### Running the Application

```bash
./salon.sh
```

### Booking Process

1. **Welcome Screen**: The application displays available services
2. **Service Selection**: Enter the number corresponding to your desired service
3. **Customer Verification**: Enter your phone number
   - If you're a new customer, you'll be prompted for your name
   - Existing customers are recognized automatically
4. **Time Selection**: Choose your preferred appointment time
5. **Confirmation**: Receive a confirmation message with appointment details

### Example Session

```
~~~~~ MY SALON ~~~~~

Welcome to My Salon, how can I help you?
1) Wig install
2) Fade Cut
3) Hair Wash
> 2

What's your phone number?
> 555-1234

What time would you like your Fade Cut, John?
> 2:30 PM

I have put you down for a Fade Cut at 2:30 PM, John.
```

## 🔧 Script Details

### Key Functions

- `MAIN_MENU()`: Primary function that handles the user interface flow
- **Input Validation**: Checks for valid service numbers and existing services
- **Customer Management**: Automatically creates new customer records when needed
- **Appointment Creation**: Inserts appointments into the database

### Database Operations

The script performs the following SQL operations:
- Retrieving available services
- Checking customer existence by phone number
- Inserting new customers
- Creating appointment records
- Formatting output data

## 🐛 Troubleshooting

### Common Issues

1. **Permission Denied**: 
   ```bash
   chmod +x salon.sh
   ```

2. **Database Connection Error**:
   - Ensure PostgreSQL is running
   - Verify the `freecodecamp` user exists
   - Check database name is `salon`

3. **Invalid Service Number**:
   - Only numbers 1-3 are valid (based on preloaded services)

### Error Messages

- "That is not a valid service number": Entered non-numeric value
- "I could not find that service": Service ID doesn't exist
- "I don't have a record for that phone number": New customer registration

## 📝 Notes

- The `appointments` table has a redundant `name` column that is not used by the script
- All times are stored as strings (VARCHAR) in the database
- Phone numbers are used as unique identifiers for customers
- The script uses `sed` for whitespace trimming in formatted output

## 🔄 Potential Improvements

1. Add appointment date along with time
2. Implement appointment cancellation functionality
3. Add employee assignment to appointments
4. Create an admin view for managing appointments
5. Add input validation for phone number format
6. Implement appointment time conflict checking

## 📄 License

This project is for educational purposes as part of the freeCodeCamp curriculum.

## 👥 Author

Salon Appointment System - Created for database and bash scripting practice.

---

*Note: This project demonstrates practical application of Bash scripting, PostgreSQL integration, and CLI application development.*
