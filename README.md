# Chakra-UI AutoComplete-adapted

> An Accessible Autocomplete Utility for [Chakra UI](github.com/chakra-ui/chakra-ui) that composes [Downshift](https://github.com/downshift-js/downshift) ComboBox

![demo-image](./img/basic.gif)

## Install

\*_Warning_ This Package is still WIP at the Moment and there might be some missing features

```bash
npm install --save chakra-ui-autocomplete-adapted
```

## Usage

- Usage Example with TSX/Typescript

```tsx
import React from 'react'
import { CUIAutoComplete } from 'chakra-ui-autocomplete'

export interface Item {
  label: string
  value: string
}
const countries = [
  { value: 'ghana', label: 'Ghana' },
  { value: 'nigeria', label: 'Nigeria' },
  { value: 'kenya', label: 'Kenya' },
  { value: 'southAfrica', label: 'South Africa' },
  { value: 'unitedStates', label: 'United States' },
  { value: 'canada', label: 'Canada' },
  { value: 'germany', label: 'Germany' }
]

export default function App() {
  const [pickerItems, setPickerItems] = React.useState(countries)
  const [selectedItems, setSelectedItems] = React.useState<Item[]>([])

  const handleCreateItem = (item: Item) => {
    setPickerItems((curr) => [...curr, item])
    setSelectedItems((curr) => [...curr, item])
  }

  const handleSelectedItemsChange = (selectedItems?: Item[]) => {
    if (selectedItems) {
      setSelectedItems(selectedItems)
    }
  }

  return (
    <CUIAutoComplete
      label='Choose preferred work locations'
      placeholder='Type a Country'
      onCreateItem={handleCreateItem}
      items={pickerItems}
      selectedItems={selectedItems}
      onSelectedItemsChange={(changes) =>
        handleSelectedItemsChange(changes.selectedItems)
      }
    />
  )
}
```

## Props

| Property               | Type     | Required        | Decscription                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------- | -------- | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| items                  | Array    | Yes             | An array of the items to be selected within the input field                                                                                                                                                                                                                                                                                                                        |
| placeholder            | string   |                 | The placeholder for the input field                                                                                                                                                                                                                                                                                                                                                |
| label                  | string   |                 | Input Form Label to describe the activity or process                                                                                                                                                                                                                                                                                                                               |
| highlightItemBg        | string   |                 | For accessibility, you can define a custom color for the highlight color when user is typing also accept props like `yellow.300` based on chakra theme provider                                                                                                                                                                                                                    |
| onCreateItem           | Function | Yes             | Function to handle creating new Item                                                                                                                                                                                                                                                                                                                                               |
| optionFilterFunc       | Function | Yes             | You can define a custom Function to handle filter logic                                                                                                                                                                                                                                                                                                                            |
| itemRenderer           | Function |                 | Custom Function that can either return a JSX Element or String, in order to control how the list items within the Dropdown is rendered                                                                                                                                                                                                                                             |
| labelStyleProps        | Object   |                 | Custom style props based on chakra-ui for labels, Example `{{ bg: 'gray.100', pt: '4'}}                                                                                                                                                                                                                                                                                            |
| inputStyleProps        | Object   |                 | Custom style props based on chakra-ui for input field, Example`{{ bg: 'gray.100', pt: '4'}}                                                                                                                                                                                                                                                                                        |
| toggleButtonStyleProps | Object   |                 | Custom style props based on chakra-ui for toggle button, Example `{{ bg: 'gray.100', pt: '4'}}                                                                                                                                                                                                                                                                                     |
| tagStyleProps          | Object   |                 | Custom style props based on chakra-ui for multi option tags, Example`{{ bg: 'gray.100', pt: '4'}}                                                                                                                                                                                                                                                                                  |
| listStyleProps         | Object   |                 | Custom style props based on chakra-ui for dropdown list, Example `{{ bg: 'gray.100', pt: '4'}}                                                                                                                                                                                                                                                                                     |
| listItemStyleProps     | Object   |                 | Custom style props based on chakra-ui for single list item in dropdown, Example`{{ bg: 'gray.100', pt: '4'}}                                                                                                                                                                                                                                                                       |
| selectedIconProps      | Object   |                 | Custom style props based on chakra-ui for the green tick icon in dropdown list, Example `{{ bg: 'gray.100', pt: '4'}}                                                                                                                                                                                                                                                              |
| icon                   | Object   | CheckCircleIcon | @chakra-ui/icons Icon to be displayed instead of CheckCircleIcon                                                                                                                                                                                                                                                                                                                   |
| hideToggleButton       | boolean  |                 | Hide the toggle button                                                                                                                                                                                                                                                                                                                                                             |
| disableCreateItem      | boolean  |                 | Disable the "create new" list Item. Default is `false`                                                                                                                                                                                                                                                                                                                             |
| createItemRenderer     | Function |                 | Custom Function that can either return a JSX Element or String, in order to control how the create new item within the Dropdown is rendered. The input value is passed as the first function parameter, Example: `` (value) => `Create ${value}` ``                                                                                                                                |
| renderCustomInput      | Function |                 | Custom function to render input from outside chakra-ui-autocomplete. Receives input props for the input element and toggleButtonProps for the toggle button. Can use this to render chakra-ui's `<InputGroup>`. Example: `(inputProps) => (<InputGroup><InputLeftElement pointerEvents="none" children={<PhoneIcon color="gray.300" />} /><Input {...inputProps} /></InputGroup>)` |

## Author

[koolamusic](https://github.com/koolamusic)

## License

MIT © [koolamusic](https://github.com/koolamusic)
