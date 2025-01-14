---
layout: default
title: "The EditableDatagrid Component"
---

# `<EditableDatagrid>`

This [Enterprise Edition](https://marmelab.com/ra-enterprise)<img class="icon" src="./img/premium.svg" /> component offers an "edit-in-place" experience in a `<Datagrid>`.

<video controls autoplay playsinline muted loop>
  <source src="https://marmelab.com/ra-enterprise/modules/assets/ra-editable-datagrid-overview.webm" type="video/webm" />
  <source src="https://marmelab.com/ra-enterprise/modules/assets/ra-editable-datagrid-overview.mp4" type="video/mp4" />
  Your browser does not support the video tag.
</video>

## Usage

First, install the `@react-admin/ra-editable-datagrid` package:

```sh
npm install --save @react-admin/ra-editable-datagrid
# or
yarn add @react-admin/ra-editable-datagrid
```

**Tip**: `ra-editable-datagrid` is hosted in a private npm registry. You need to subscribe to one of the [Enterprise Edition](https://marmelab.com/ra-enterprise/) plans to access this package.

Then, use `<EditableDatagrid>` as a child of a react-admin `<List>`, `<ReferenceManyField>`, or any other component that creates a `ListContext`.

```jsx
import {
    List,
    TextField,
    TextInput,
    DateField,
    DateInput,
    SelectField,
    SelectInput,
    required,
} from 'react-admin';
import { EditableDatagrid, RowForm } from '@react-admin/ra-editable-datagrid';

const professionChoices = [
    { id: 'actor', name: 'Actor' },
    { id: 'singer', name: 'Singer' },
    { id: 'other', name: 'Other' },
];

const ArtistList = () => (
    <List hasCreate empty={false}>
        <EditableDatagrid
            mutationMode="undoable"
            createForm={<ArtistForm />}
            editForm={<ArtistForm />}
        >
            <TextField source="id" />
            <TextField source="firstname" />
            <TextField source="name" />
            <DateField source="dob" label="born" />
            <SelectField
                source="prof"
                label="Profession"
                choices={professionChoices}
            />
        </EditableDatagrid>
    </List>
);

const ArtistForm = () => (
    <RowForm>
        <TextField source="id" />
        <TextInput source="firstname" validate={required()} />
        <TextInput source="name" validate={required()} />
        <DateInput source="dob" label="born" validate={required()} />
        <SelectInput
            source="prof"
            label="Profession"
            choices={professionChoices}
        />
    </RowForm>
);
```

`<EditableDatagrid>` is a drop-in replacement for `<Datagrid>`. It expects 2 additional props: `createForm` and `editForm`, the components to be displayed when a user creates or edits a row. The `<RowForm>` component allows to create such forms using react-admin Input components. 


Check [the `ra-editable-datagrid` documentation](https://marmelab.com/ra-enterprise/modules/ra-editable-datagrid) for more details.
