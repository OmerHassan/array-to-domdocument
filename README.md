# array-to-domdocument
DOM class provides the following static methods for converting a PHP array to DOMDocument or vice versa:

```
DOM::arrayToDOMDocument(array $source, $rootTagName = 'root')
DOM::arrayToXMLString(array $source, $rootTagName = 'root', $formatOutput = true)
DOM::domDocumentToArray(DOMDocument $document)
DOM::xmlStringToArray($xmlString)
```

# Example
```
require_once 'DOM.php';

$xmlString = '
   <root>
     <book isbn="978-3-16-148410-0">
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
     <book isbn="978-3-16-148410-0">Title2</book>
   </root>
';

$array = DOM::xmlStringToArray($xmlString);

print_r($array);
```
Output:
```
Array
(
  [book] => Array
    (
      [0] => Array
        (
          [author] => Author0
          [title] => Title0
          [publisher] => Publisher0
          [__attributes__] => Array
            (
              [isbn] => 978-3-16-148410-0
            )
        )
      [1] => Array
        (
          [author] => Array
            (
              [0] => Author1
              [1] => Author2
            )
          [title] => Title1
          [publisher] => Publisher1
        )
      [2] => Array
        (
          [__attributes__] => Array
            (
              [isbn] => 978-3-16-148410-0
            )
          [__content__] => Title2
        )
    )
)
```
