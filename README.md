# Investment Calculator

A modern, full-stack investment calculator built with Node.js, Express, PostgreSQL, and EJS templating. This application allows users to calculate compound interest, SIP returns, and includes a contact form that saves submissions to a PostgreSQL database.

## Features

- **Investment Calculator**: Calculate compound interest and SIP returns
- **Interactive Charts**: Visual representation of investment growth using Chart.js
- **Contact Form**: Save user inquiries to PostgreSQL database
- **Responsive Design**: Modern UI with Bootstrap 5 and custom CSS
- **Real-time Calculations**: Instant results with AJAX requests
- **Form Validation**: Client-side and server-side validation
- **Security**: Helmet.js for security headers and rate limiting

## Tech Stack

- **Backend**: Node.js, Express.js
- **Database**: PostgreSQL with pg library
- **Frontend**: EJS templating, Bootstrap 5, Chart.js
- **Security**: Helmet.js, CORS, Rate limiting
- **Styling**: Custom CSS with modern gradients and animations

## Prerequisites

Before running this application, make sure you have the following installed:

- Node.js (v14 or higher)
- PostgreSQL (v12 or higher)
- pgAdmin (for database management)

## Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd investment-calculator
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up PostgreSQL Database**
   - Open pgAdmin
   - Create a new database named `investment_calculator`
   - Note down your database credentials

4. **Configure Environment Variables**
   - Rename `.env.example` to `.env` (if it exists)
   - Update the `.env` file with your database credentials:
   ```env
   PORT=3000
   NODE_ENV=development
   DB_HOST=localhost
   DB_PORT=5432
   DB_NAME=investment_calculator
   DB_USER=postgres
   DB_PASSWORD=your_password_here
   DATABASE_URL=postgresql://postgres:your_password_here@localhost:5432/investment_calculator
   ```

5. **Start the application**
   ```bash
   # Development mode with nodemon
   npm run dev
   
   # Production mode
   npm start
   ```

6. **Access the application**
   - Open your browser and go to `http://localhost:3000`

## Database Setup

The application will automatically create the required tables when it starts. The main table is:

```sql
CREATE TABLE contacts (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL,
    phone VARCHAR(20),
    message TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## API Endpoints

### Investment Calculator
- `POST /calculate` - Calculate investment returns
  - Body: `{ principal, rate, time, frequency }`

### Contact Form
- `POST /contact/submit` - Submit contact form
  - Body: `{ name, email, phone, message }`
- `GET /contact/all` - Get all contacts (admin)
- `GET /contact/:id` - Get specific contact
- `DELETE /contact/:id` - Delete contact

## Project Structure

```
investment-calculator/
├── src/
│   ├── config/
│   │   └── database.js          # Database configuration
│   ├── controllers/
│   │   ├── indexController.js   # Main calculator logic
│   │   └── contactController.js # Contact form handling
│   ├── models/
│   │   └── Contact.js           # Database model
│   ├── routes/
│   │   ├── index.js             # Main routes
│   │   └── contact.js           # Contact routes
│   ├── views/
│   │   ├── layout.ejs           # Main layout template
│   │   ├── index.ejs            # Home page
│   │   └── error.ejs            # Error page
│   ├── public/
│   │   ├── css/
│   │   │   └── style.css        # Custom styles
│   │   └── js/
│   │       └── main.js          # Frontend JavaScript
│   └── server.js                # Main server file
├── .env                         # Environment variables
├── package.json                 # Dependencies and scripts
└── README.md                    # This file
```

## Usage

1. **Investment Calculator**
   - Enter the principal amount
   - Set the interest rate (1-50%)
   - Choose the time period (1-50 years)
   - Select compounding frequency
   - Click "Calculate Investment" to see results

2. **Contact Form**
   - Fill in your name, email, and message
   - Optionally add a phone number
   - Submit to save to the database

## Features in Detail

### Investment Calculations
- **Compound Interest**: Calculates final amount and interest earned
- **SIP (Systematic Investment Plan)**: Shows monthly investment growth
- **Interactive Charts**: Visual representation of investment growth over time
- **Multiple Frequencies**: Annual, quarterly, and monthly compounding

### Contact Management
- **Form Validation**: Client-side and server-side validation
- **Database Storage**: All submissions saved to PostgreSQL
- **Email Validation**: Proper email format checking
- **Success/Error Messages**: User-friendly feedback

### Security Features
- **Helmet.js**: Security headers
- **Rate Limiting**: Prevents abuse
- **CORS**: Cross-origin resource sharing
- **Input Validation**: Sanitized inputs

## Customization

### Styling
- Modify `src/public/css/style.css` for custom styling
- Update color schemes in the CSS variables
- Add new animations or effects

### Calculations
- Edit `src/controllers/indexController.js` for calculation logic
- Modify the investment formulas as needed
- Add new calculation types

### Database
- Update `src/models/Contact.js` for database operations
- Add new fields to the contacts table
- Create additional tables as needed

## Troubleshooting

### Common Issues

1. **Database Connection Error**
   - Check PostgreSQL is running
   - Verify database credentials in `.env`
   - Ensure database exists

2. **Port Already in Use**
   - Change PORT in `.env` file
   - Kill existing process on port 3000

3. **Module Not Found**
   - Run `npm install` to install dependencies
   - Check `package.json` for missing dependencies

### Debug Mode
Set `NODE_ENV=development` in `.env` for detailed error messages and stack traces.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the ISC License.

## Support

For support or questions, please open an issue in the repository or contact the development team. 