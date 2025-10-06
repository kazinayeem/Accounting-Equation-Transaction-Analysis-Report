# Streamlined Accounting Equation Analysis

## Installation

This project is a web-based application and does not require any installation. Simply open the `index.html` file in a web browser to use the application.

## Usage

1. Enter your list of transactions in the "AI Transaction Entry & Analysis" panel.
2. Click the "Fill Entries with AI" button to have the AI classify the changes into the 9 accounts automatically.
3. The table will be populated with the transaction details and the accounting equation will be analyzed.
4. Use the control panel buttons to add new transactions, clear the table, export the data to Excel, or export a PDF report.

## API

The application uses the Gemini API from Google Cloud to classify the transactions. The API is called with the following payload:

```json
{
  "contents": [
    {
      "parts": [
        {
          "text": "Your list of transactions"
        }
      ]
    }
  ],
  "systemInstruction": {
    "parts": [
      {
        "text": "System prompt for the API"
      }
    ]
  },
  "generationConfig": {
    "responseMimeType": "application/json",
    "responseSchema": {
      "type": "ARRAY",
      "items": {
        "type": "OBJECT",
        "properties": {
          "description": {
            "type": "STRING",
            "description": "A concise description of the transaction."
          },
          "Cash": {
            "type": "NUMBER",
            "description": "Change in Cash (e.g., +1000 or -500)"
          },
          "A/c Receivable": {
            "type": "NUMBER",
            "description": "Change in Accounts Receivable"
          },
          "Supplies": {
            "type": "NUMBER",
            "description": "Change in Supplies"
          },
          "Equipment": {
            "type": "NUMBER",
            "description": "Change in Equipment"
          },
          "A/c Payable": {
            "type": "NUMBER",
            "description": "Change in Accounts Payable"
          },
          "Owner's Capital": {
            "type": "NUMBER",
            "description": "Change in Owner's Capital (Investment)."
          },
          "Revenue": {
            "type": "NUMBER",
            "description": "Change in Revenue (Earnings)."
          },
          "Expenses": {
            "type": "NUMBER",
            "description": "Change in Expenses (Costs incurred)."
          },
          "Withdrawals": {
            "type": "NUMBER",
            "description": "Change in Withdrawals (Personal use)."
          }
        },
        "required": [
          "description",
          "Cash",
          "A/c Receivable",
          "Supplies",
          "Equipment",
          "A/c Payable",
          "Owner's Capital",
          "Revenue",
          "Expenses",
          "Withdrawals"
        ]
      }
    }
  }
}
```

## Contributing

Contributions to this project are welcome. If you find any issues or have suggestions for improvements, please create a new issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).

## Testing

The application has been tested manually. No automated tests are currently available.