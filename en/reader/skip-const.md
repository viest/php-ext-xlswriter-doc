# Skip mode constants

These constants control whether the reader emits blank cells, blank rows, and empty values. Pass them as a bitmask to `setType()` / `setGlobalType()`.

```php
const SKIP_NONE        = 0x00;  // emit every cell and row
const SKIP_EMPTY_ROW   = 0x01;  // drop rows that contain no data
const SKIP_EMPTY_CELLS = 0x02;  // drop cells that have no data
                                // (an XML cell with no value is dropped, even
                                //  if it exists in the sheet structure)
const SKIP_EMPTY_VALUE = 0x100; // drop cells whose value is an empty string
```
