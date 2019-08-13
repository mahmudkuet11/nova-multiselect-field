# Nova Multiselect

This [Laravel Nova](https://nova.laravel.com) package adds a multiselect to Nova's arsenal of fields.

## Screenshots

![Detail View](docs/detail.png)

![Form View](docs/form.png)

![Index View](docs/index.png)

## Installation

Install the package in a Laravel Nova project via Composer:

```bash
composer require mahmudkuet11/nova-multiselect-field
```

## Usage

The field is used similarly to Nova's native Select field. The field type in the database should be text-based (ie `string`, `text` or `varchar`), selected values are stored as a JSON array.

```php
use Mahmud\MultiselectField\Multiselect;

public function fields(Request $request)
{
    return [
      Multiselect
        ::make('Favourite football teams', 'football_teams')
        ->options([
          'liverpool' => 'Liverpool FC',
          'tottenham' => 'Tottenham Hotspur',
          'bvb' => 'Borussia Dortmund',
          'bayern' => 'FC Bayern Munich',
          'barcelona' => 'FC Barcelona',
          'juventus' => 'Juventus FC',
          'psg' => 'Paris Saint-Germain FC',
        ])

        // Optional:
        ->placeholder('Choose football teams')
        ->max(4)
        ->optionsLimit(5)
    ];
}
```

## Options

Possible options you can pass to the field using the option name as a function, ie `->placeholder('Choose peanuts')`.

| Option                        | type     | default    | description                                                                                                                                                                  |
| ----------------------------- | -------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `options`                     | Array    | []         | Options in an array as key-value pairs (`['id' => 'value']`).                                                                                                                |
| `placeholder`                 | String   | Field name | The placeholder string for the input.                                                                                                                                        |
| `max`                         | Number   | Infinite   | The maximum number of options a user can select.                                                                                                                             |
| `optionsLimit`                | Number   | 1000       | The maximum number of options displayed at once. Other options are still accessible through searching.                                                                       |
| `resolveForPageResponseUsing` | Callable | null       | Only for use in conjunction with [Page Manager](https://github.com/optimistdigital/nova-page-manager). Allows you to format the value before it is returned through the API. |
| `nullable`                    | Boolean  | false      | If the field is nullable an empty select will result in `null` else an empty array (`[]`) is stored.                                                                         |

## Credits

- [optimistdigital](https://github.com/optimistdigital/nova-multiselect-field)
- [shentao/vue-multiselect](https://vue-multiselect.js.org)

## License

This project is open-sourced software licensed under the [MIT license](LICENSE.md).
