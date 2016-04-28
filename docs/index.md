`index` (component)
===================

A typeahead that, when an option is selected, instead of simply filling
the text entry widget, prepends a renderable "token", that may be deleted
by pressing backspace on the beginning of the line with the keyboard.

Example usage:

     import StructuredFilter from 'react-structured-filter';

     <StructuredFilter
       placeholder="Search..."
       options={[
         {category:"Name",type:"text"},
         {category:"Price",type:"number"},
       ]}
     />

Props
-----

### `customClasses`

An object containing custom class names for child elements. Useful for
integrating with 3rd party UI kits. Allowed Keys: `input`, `results`,
`listItem`, `listAnchor`, `typeahead`, `hover`

Example:

    {
      input: 'filter-tokenizer-text-input',
      results: 'filter-tokenizer-list__container',
      listItem: 'filter-tokenizer-list__item'
    }

type: `object`  
defaultValue: `{}`  


### `defaultSelected`

A set of values of tokens to be loaded on first render. Each token should
be an object with a `category`, `operator`, and `value` key.

Example:

    [
      {
        category: 'Industry',
        operator: '==',
        value: 'Books',
      },
      {
        category: 'IPO',
        operator: '<',
        value: '1999-12-31',
      },
      {
        category: 'Name',
        operator: 'contains',
        value: 'Nabokov',
      },
    ]

type: `array`  
defaultValue: `[]`  


### `defaultValue`

A default value used when the component has no value. If it matches any
options a option list will show.

type: `string`  
defaultValue: `''`  


### `onTokenAdd`

Event handler triggered whenever a token is added. Params: `(addedToken)`

type: `func`  
defaultValue: `function() {}`  


### `onTokenRemove`

Event handler triggered whenever a token is removed. Params: `(removedToken)`

type: `func`  
defaultValue: `function() {}`  


### `options`

An array of structures with the components `category` and `type`

* _category_: Name of the first thing the user types.
* _type_: This can be one of the following:
  * _text_: Arbitrary text for the value. No autocomplete options.
    Operator choices will be: `==`, `!=`, `contains`, `!contains`.
  * _textoptions_: You must additionally pass an options value which
    will be a function that returns the list of options choices as an
    array (for example `function getOptions() {return ["MSFT", "AAPL",
    "GOOG"]}`). Operator choices will be: `==`, `!=`.
  * _number_: Arbitrary text for the value. No autocomplete options.
    Operator choices will be: `==`, `!=`, `<`, `<=`, `>`, `>=`.
  * _date_: Shows a calendar and the input must be of the form
    `YYYY-MM-DD`. Operator choices will be: `==`, `!=`, `<`, `<=`, `>`,
    `>=`.

Example:

    [
      {
        "category": "Symbol",
        "type": "textoptions",
        "options": function() {return ["MSFT", "AAPL", "GOOG"]}
      },
      {
        "category": "Name",
        "type": "text"
      },
      {
        "category": "Price",
        "type": "number"
      },
      {
        "category": "MarketCap",
        "type": "number"
      },
      {
        "category": "IPO",
        "type": "date"
      }
    ]

type: `array`  
defaultValue: `[]`  


### `placeholder`

Placeholder text for the typeahead input.

type: `string`  
defaultValue: `''`  
