# Repository of all Locale Identifiers



Since I started using functions related to international settings I have realized the lack of a complete repository of Local codes.
So I committed to building this repository for myself, which I also make available to anyone who needs it.

#### Standards

The repository includes identification codes that refer to the [RFC4646](https://www.rfc-editor.org/rfc/rfc4646) standard characterized by the separation character - (line) and also those of the [posix](https://en.wikipedia.org/wiki/Locale_(computer_software)#POSIX_platforms) / [XPG](https://sourceware.org/glibc/manual/2.41/html_node/Locale-Names.html) standard characterized by the separator _ (underscore).

#### Available formats

The following formats are available:

- a **csv file**, with the character `tab` (#9) as the field separator.

  - The first row is the headers of column
  - Field in row is:
    - `id`: code id of Locale identifier;
    - `Language / country`: description of language / country;
    - `country`:  2-characters iso country code associated to language;
    - `standard`: reference to standards code;
    - `note`: some reference notes.

- a **php file** with a self-instantiated class assigned to identifier `$localeIdentifiers`, that integrates the repository and query functions.

  <u>Usage example</u>:

  ```php
  <?php
  include 'LocaleIdentifiersRepo.php';
  
  echo ($localeIdentifiers->isValid('it') ? "it exists" : "not exist") . PHP_EOL;
  //result: it exists
  
  echo "IT = " . $localeIdentifiers->getLanguageDescription('it') . PHP_EOL;
  //result: Italian (Italy)
  
  print_r($localeIdentifiers->getIdentifierOfCountry('it'));
  //result:
  //array [IT => [id=>ca-it, dsc=>Catalan (Italy) ...],
  //               [id=>de-it, dsc=>German (Italy) ...],
  //               [id=>it-IT, dsc=>Italian (Italy) ...],
  //               ...
  //        ]
  ```

- a **javascript** file with the repository loaded into a map() object named `localeIdentifiers`.

  <u>Usage example</u>:

  ```js
  console.log(localeIdentifiers.has('it_IT.UTF-8'));
  //result: True
  
  console.log(localeIdentifiers.get('it_IT.UTF-8').get('dsc'));
  //result: Italian (Italy)
  
  console.log(localeIdentifiers.get('it_IT.UTF-8').get('country'));
  //result: IT
  ```

  

Si prega di segnalare eventuali errori.

