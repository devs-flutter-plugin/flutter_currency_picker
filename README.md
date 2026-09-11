# Currency picker

A Flutter package to select a currency from a list of currencies.

This fork targets Flutter 3.47+ and uses Flutter's standalone `material_ui` package instead of the legacy `package:flutter/material.dart` library.

<img height="600" alt="Currency picker screenshot" src="https://raw.githubusercontent.com/devs-flutter-plugin/flutter_currency_picker/master/assets/ReadMe%20Screenshot.png">

## Requirements

- Flutter `>=3.47.0`
- Dart `>=3.13.0`
- `material_ui: ^1.2.0`

## Getting Started

Add the maintained fork and Material UI to your `pubspec.yaml`:

```yaml
dependencies:
  currency_picker:
    git:
      url: https://github.com/devs-flutter-plugin/flutter_currency_picker.git
  material_ui: ^1.2.0
```

Import the package and the standalone Material library:

```dart
import 'package:currency_picker/currency_picker.dart';
import 'package:material_ui/material_ui.dart';
```

Show the picker using `showCurrencyPicker`:

```dart
showCurrencyPicker(
  context: context,
  showFlag: true,
  showCurrencyName: true,
  showCurrencyCode: true,
  onSelect: (Currency currency) {
    print('Select currency: ${currency.name}');
  },
);
```

### Parameters

- `onSelect`: Called when a currency is selected. The currency picker passes the new value to the callback.
- `showFlag`: Shows the flag for each currency. Defaults to `true`.
- `searchHint`: Custom hint for the search `TextField`.
- `showCurrencyName`: Shows or hides the currency name. Defaults to `true`.
- `showCurrencyCode`: Shows or hides the currency code. Defaults to `true`.
- `showSearchField`: Shows or hides the search `TextField`. Defaults to `true`.
- `currencyFilter`: Filters the available currencies by currency code.
- `favorite`: Shows selected currencies at the top of the list.
- `theme`: Customizes the currency list bottom sheet.

```dart
showCurrencyPicker(
  context: context,
  theme: CurrencyPickerThemeData(
    flagSize: 25,
    titleTextStyle: const TextStyle(fontSize: 17),
    subtitleTextStyle: TextStyle(
      fontSize: 15,
      color: Theme.of(context).hintColor,
    ),
    bottomSheetHeight: MediaQuery.of(context).size.height / 2,
    inputDecoration: InputDecoration(
      labelText: 'Search',
      hintText: 'Start typing to search',
      prefixIcon: const Icon(Icons.search),
      border: OutlineInputBorder(
        borderSide: BorderSide(
          color: const Color(0xFF8C98A8).withValues(alpha: 0.2),
        ),
      ),
    ),
  ),
  onSelect: (Currency currency) {
    print('Select currency: ${currency.name}');
  },
);
```

## Material UI migration

Version 3.x exposes standalone `material_ui` types in the public API. Applications using this fork should migrate their own Material imports from:

```dart
import 'package:flutter/material.dart';
```

to:

```dart
import 'package:material_ui/material_ui.dart';
```

Flutter also provides the automated migration:

```bash
dart fix --apply --code=migrate_design_widgets
```

## Contributions

Contributions are welcome. Open an issue or pull request in this repository for fixes and improvements.
