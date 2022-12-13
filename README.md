## Demo - (https://joyful-valkyrie-eb30c6.netlify.app/)

#### Quick Start:

* Install from npm (https://www.npmjs.com/package/vv3-data-table).
* Clone or [download](https://github.com/Sabih0199/vue-vuetify3-data-table/archive/refs/heads/main.zip) this repo. (if you download, unzip the file to a directory.)
* On the command line in the top directory of this repo, run `npm run dev`
* Visit the application with your browser at http://127.0.0.1:3000/

### Features:
* Render Jsx Element.
* Sorts and Pagination.

### Todo:
* Filter by Search

### Basic Example:
```
const COLUMNS = {
  ID: {
    label: "Id",
    key: "id"
  }
};

const DummyData = [
    {
        id: 1,
        fname: "Allan",
        lname: "Malthus",
        email: "amalthus0@odnoklassniki.ru",
        gender: "Male",
        ipa: "65.132.216.60"
    }
]

<data-table :data="DummyData" :config="[
        {
          title: COLUMNS.ID,
          render: (data) => data.id,
          sortable: true //enable sort for this column
        }
    ]
/>
```

## Screenshots:
![Jenkins pipeline](https://live.staticflickr.com/65535/52562237268_7e5587457f_o.png)

![Zap attach proxy](https://live.staticflickr.com/65535/52561242872_c4f845d13e_o.png)

![SonarQube analysis](https://live.staticflickr.com/65535/52561242877_f7f68c853c_o.png)
