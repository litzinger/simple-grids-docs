---
title: FAQs
taxonomy:
    category: docs
---

### What makes Simple Grid different than the native Grid field?
Simple Grid can be defined as a column in a Grid field. The native Grid field can not be nested inside of itself. Simple Grid saves its data
as a JSON object, thus there is no complicated data storage model, which means it can easily be nested inside of Grid, Bloqs, or Fluid.

### What column types can Simple Grid have?
Simple Grid only has Text, Textarea, File, and Toggle fields.

### Why don't other Grid compatible fieldtypes work in Simple Grid?
See the previous question. Simple Grid is just that, its a simplified version of the Grid field and it will not support all fieldtypes.

### Why can't I configure options for the textarea, or file column?
Remember, this is **Simple** Grid. Adding options for each column goes beyond the scope of Simple Grid.

### Are there plans to add additional fieldtype support?
Not at this time. A fieldtype must meet the following conditions to be supported by Simple Grid:

1. Save data as a string. No complicated data such as arrays.
2. Be able to function with out any field or column settings.
3. Be easy to add to the codebase and easy to maintain.

This isn't to say additional fieldtypes won't be supported, but they will be very, very carefully reviewed before support is added.

### If I'm an add-on developer or want to add my own column type, how do I do that?
Short answer, you don't. There is no API to add column types. Long answer, if you wanted to add support and send us a diff of the changes we'll review them. Also see the previous question about adding new fieldtypes.

### Can I rename or change the order of columns in Simple Grid once the field is created?
Yes you can. Columns are saved in the JSON with IDs, so you can rename or reorder them (this was a limitation of the old Nolan fieldtype).

### Can I define column names for Simple Table?
Sort of. When you create a Simple Table field you can enter the value of the first row of columns as a starting point.
This value will pre-populate when the field loads in the entry publish page, however, the user can change or remove the
values since all table cells are textarea fields.

### How many rows and columns can I add to Simple Table?
As many as you want.