# array-to-domdocument
The class DOM contains these public static methods:
```
arrayToDOMDocument(array $source, $rootTagName = 'root')
arrayToXMLString(array $source, $rootTagName = 'root', $formatOutput = true)

domDocumentToArray(DOMDocument $document)
xmlStringToArray($xmlString)
```

# Example #
```
require_once 'DOM.php';

$source['book'][0][DOM::ATTRIBUTES]['isbn'] = '978-3-16-148410-0';
$source['book'][0][DOM::ATTRIBUTES]['publish-date'] = '2002-03-25';
$source['book'][0]['author'] = 'Author0';
$source['book'][0]['title'] = 'Title0';
$source['book'][0]['publisher'] = 'Publisher0';

$source['book'][1]['author'][0] = 'Author1';
$source['book'][1]['author'][1] = 'Author2';
$source['book'][1]['title'] = 'Title1';
$source['book'][1]['publisher'] = 'Publisher1';

$source['book'][2][DOM::ATTRIBUTES]['isbn'] = '978-3-16-148410-0';
$source['book'][2][DOM::ATTRIBUTES]['publish-date'] = '2002-03-25';
$source['book'][2][DOM::CONTENT] = 'Title2';

echo $xml = DOM::arrayToXMLString($source);

print_r(DOM::xmlStringToArray($xml));
```
Output:
```
<?xml version="1.0"?>
<root>
  <book isbn="978-3-16-148410-0" publish-date="2002-03-25">
    <author>Author0</author>
    <title>Title0</title>
    <publisher>Publisher0</publisher>
  </book>
  <book>
    <author>Author1</author>
    <author>Author2</author>
    <title>Title1</title>
    <publisher>Publisher1</publisher>
  </book>
  <book isbn="978-3-16-148410-0" publish-date="2002-03-25">Title2</book>
</root>
Array
(
  [book] => Array
    (
      [0] => Array
        (
          [__attributes__] => Array
            (
              [isbn] => 978-3-16-148410-0
              [publish-date] => 2002-03-25
            )
          [author] => Array
            (
              [0] => Array
                (
                  [__content__] => Author0
                )
            )
          [title] => Array
            (
              [0] => Array
                (
                  [__content__] => Title0
                )
            )
          [publisher] => Array
            (
              [0] => Array
                (
                  [__content__] => Publisher0
                )
            )
        )
      [1] => Array
        (
          [author] => Array
            (
              [0] => Array
                (
                  [__content__] => Author1
                )
              [1] => Array
                (
                  [__content__] => Author2
                )
            )
          [title] => Array
            (
              [0] => Array
                (
                  [__content__] => Title1
                )
            )
          [publisher] => Array
            (
              [0] => Array
                (
                  [__content__] => Publisher1
                )
            )
        )
      [2] => Array
        (
          [__attributes__] => Array
            (
              [isbn] => 978-3-16-148410-0
              [publish-date] => 2002-03-25
            )
          [__content__] => Title2
        )
    )
)
```
