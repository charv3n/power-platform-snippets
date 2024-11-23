# Power Fx: Number to Words Converter for Power Apps

This repository contains a Power Fx code snippet for converting numeric inputs into their word representation, complete with place values (e.g., "Million," "Thousand") and customizable currency terms like "Dollar" and "Cents." It is ideal for use in Power Apps to display financial values in a human-readable format for invoices, reports, or forms.

## Features
- Converts numbers up to the trillions into words.
- Includes place values for large numbers, such as "Million" and "Billion."
- Handles decimal places to represent values like "Cents."
- Supports customization for different currencies and formats.
- Designed for systems using English or similar number-to-text conventions.

## Example Outputs
1. **Input:** `1234567.89`  
   **Output:** `"One Million Two Hundred Thirty-Four Thousand Five Hundred Sixty-Seven Dollar and Eighty-Nine Cents"`

2. **Input:** `0.50`  
   **Output:** `"Zero Dollar and Fifty Cents"`

3. **Input:** `1000000`  
   **Output:** `"One Million Dollar"`

4. **Input:** `0`  
   **Output:** `"Zero Dollar"`

## Limitations
- Works for English or similar number-to-word systems.
- Does not handle negative numbers or values larger than trillions.
- Requires properly formatted numeric input (no special characters).
- Limited support for localization beyond currency term adjustments.

## How to Use
1. Copy the Power Fx code from the [code file](link-to-code).
2. Paste it into your Power Apps app (e.g., within a label's formula or a function).
3. Test with sample inputs to ensure it works for your specific use case.
4. Customize currency terms or arrays for different formats or locales.

## How to Customize
- Modify `_ones`, `_tens`, and `_places` arrays to adapt the output for other languages or systems.
- Update the currency terms, such as "Dollar" and "Cents," to suit your application.

## Contributing
Contributions are welcome! If you have ideas for improvements, support for additional languages, or features, feel free to:
- Open an [issue](https://github.com/your-username/PowerFx-Number-to-Words/issues) to share your feedback.
- Submit a pull request with your changes.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Feedback
If you find this snippet helpful or have suggestions for improvements, feel free to reach out or create an issue in this repository.

---

Thank you for using Power Fx: Number to Words with Currency Formatting!
