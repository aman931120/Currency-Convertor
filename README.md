# Currency Converter

A simple currency converter web application built using React.js. This application allows users to convert an amount from one currency to another using real-time exchange rates.

## Features
- Convert between multiple currencies
- Swap currencies easily
- Responsive UI with a modern design
- Background image for an enhanced visual experience
- Utilizes React hooks for state management

## Technologies Used
- React.js
- Tailwind CSS
- Custom Hooks

## Installation & Setup
To set up and run this project locally, follow these steps:

1. **Clone the repository**
   ```sh
   git clone https://github.com/your-username/currency-converter.git
   cd currency-converter
   ```
2. **Install dependencies**
   ```sh
   npm install
   ```
3. **Start the development server**
   ```sh
   npm start
   ```

## Project Structure
```
📂 currency-converter
├── 📂 src
│   ├── 📂 components      # Reusable components
│   ├── 📂 hooks           # Custom hooks
│   ├── 📜 App.jsx         # Main application file
│   ├── 📜 useCurrencyInfo.js # Custom hook for fetching currency data
│   ├── 📜 index.js        # Entry point
│   ├── 📜 App.css         # Styling
├── 📜 package.json        # Project dependencies
├── 📜 README.md           # Project documentation
```

## How the Project Works
### 1. **Fetching Currency Data**
The project uses a custom hook `useCurrencyInfo.js` to fetch real-time exchange rates based on the selected currency.
```js
import { useEffect, useState } from "react";

function useCurrencyInfo(baseCurrency) {
  const [currencyData, setCurrencyData] = useState({});

  useEffect(() => {
    fetch(`https://api.exchangerate-api.com/v4/latest/${baseCurrency}`)
      .then(response => response.json())
      .then(data => setCurrencyData(data.rates));
  }, [baseCurrency]);

  return currencyData;
}

export default useCurrencyInfo;
```

### 2. **State Management**
The `App.jsx` file maintains the state using `useState` hook:
```js
const [amount, setAmount] = useState(0);
const [from, setFrom] = useState("usd");
const [to, setTo] = useState("inr");
const [convertedAmount, setConvertedAmount] = useState(0);
```

### 3. **Handling Conversion**
A function is used to calculate the converted amount:
```js
const convert = () => {
  setConvertedAmount(amount * currencyInfo[to]);
};
```

### 4. **Swapping Currencies**
A simple function swaps the currency values:
```js
const swap = () => {
  setFrom(to);
  setTo(from);
  setConvertedAmount(amount);
  setAmount(convertedAmount);
};
```

### 5. **Reusable Components**
The `InputBox` component is used to handle input fields dynamically.
```js
<InputBox
  label="From"
  amount={amount}
  currencyOptions={options}
  onCurrencyChange={(currency) => setFrom(currency)}
  onAmmountChange={(amount) => setAmount(amount)}
  selectCurrency={from}
/>
```

## Usage
1. Enter the amount you wish to convert.
2. Select the currency you want to convert from.
3. Select the currency you want to convert to.
4. Click the **Convert** button to get the converted amount.
5. Use the **Swap** button to quickly switch between the selected currencies.

## Contribution
If you want to contribute to this project:
1. Fork the repository.
2. Create a new branch: `git checkout -b feature-branch`
3. Make your changes and commit: `git commit -m 'Added a new feature'`
4. Push the changes: `git push origin feature-branch`
5. Create a Pull Request.

## License
This project is open-source and available under the [MIT License](LICENSE).

## Contact
For any queries or issues, feel free to reach out at [your-email@example.com](mailto:akt9802@gmail.com).

