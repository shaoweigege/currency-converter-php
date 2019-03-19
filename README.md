# currency-converter-php

This project implements a simple function to convert currencies using open APIs that do not require access keys

## Usage

Import the 'CurrencyConverter.php' file into your project

    require('CurrencyConverter.php'); 

Call the 'convert' method and it will return the converted currency value

    App\CurrencyConverter::convert();

By default the function will convert US dollars into Brazilian real, but the base currency and the currency for conversion can be specified by passing a settings parameter:

    App\CurrencyConverter::convert(['from' => 'EUR', 'to' => 'USD']);

The settings that can be passed in the second parameter are:

| parameter | definition                                                                                                                                                                                                                                                                                                                                                                     |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| from      | Defines the base currency for conversion. The default value is 'USD'.                                                                                                                                                                                                                                                                                                          |
| to        | Defines the target currency. The default value is 'BRL'.                                                                                                                                                                                                                                                                                                                       |
| amount    | Sets the amount of base currency to convert to the target currency. The default value is 1.                                                                                                                                                                                                                                                                                    |
| api       | Defines the API that will be used. If the defined api is not available or has an error, the next API in the list will be selected automatically. The APIs available by default are: ['ratesapi'](https://ratesapi.io/), ['exchangeratesapi'](https://exchangeratesapi.io/), ['currencyconverterapi'](https://free.currencyconverterapi.com/). The default value is 'ratesapi'. |

Examples:

    App\CurrencyConverter::convert(['from' => 'EUR', 'to' => 'USD', 'amount' => 100, 'api' => 'currencyconverterapi']);

    App\CurrencyConverter::convert(['from' => 'EUR', 'amount' => 23]);

    App\CurrencyConverter::convert(['api' => 'exchangeratesapi']);

If the selected API is not available or has an error, the next API will be selected and the process will be restarted until the function succeeds in the response. If none of the APIs is available the function will return an array with errors from each API

## License

This project is licensed under the MIT License - see the LICENSE.md file for details

## Acknowledgments

For more details consult the source code and documentation for each API used in this.

APIs used:

-   <https://ratesapi.io/>
-   <https://exchangeratesapi.io/>
-   <https://free.currencyconverterapi.com/>
