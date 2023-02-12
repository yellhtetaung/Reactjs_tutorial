# Reactjs Tutorial

## Installation

```bash
npx create-react-app my-app
cd my-app
npm start
```

### About Components

```jsx
import React from "react";
import ReactDOM from "react-dom";

function Greeting() {
  return <h1>This is reactjs Tutorial</h1>; // JSX
}

ReactDOM.render(<Greeting />, document.getElementById("root"));
```

```jsx
ReactDOM.render(<Greeting />, document.getElementById("root"));
```

render method သည် parameter 2 ခု လက်ခံတယ်။ first parameter သည် ကိုယ်သုံးချင်တဲ့ component ကိုထည့်ရပါတယ်။ second
parameter မှာကတော့ ./public/index.html ထဲက root ကိုထည့်ပေးရမှာဖြစ်ပါတယ်။ reactjs သည် single page application
ဖြစ်တဲ့အတွက်ကြောင့် HTML file သည် တစ်ခုတည်းရှိပါတယ်။ Reactjs သည် HTML syntax တွေကို HTML လို့ မခေါ်ပါဘူး။ **_JSX_** လို့ ခေါ်ပါတယ်။

---

### How to work function in return html code

```jsx
import React from "react";
import ReactDOM from "react-dom";

function Greeting() {
  return React.createElement("h1", {}, "Hello world");
}

ReactDOM.render(<Greeting />, document.getElementById("root"));
```

```jsx
React.createElement("h1", {}, "Hello world");
```

- First parameter is html tag.
- Second parameter is props.
- Third parameter is content.

---

```jsx
import React from "react";
import ReactDOM from "react-dom";

function Greeting() {
  return (
    <div>
      <h1>This is reactjs tutorial</h1>
      <p>This is paragraph</p>
    </div>
  );
}

ReactDOM.render(<Greeting />, document.getElementById("root"));
```

HTML element တွေကို တစ်ခုထက်ပိုသုံးချင်ရင် container(div) တစ်ခုထဲကိုထည့်ပြီး သုံးပေးရပါတယ်။ react သည် component mount လုပ်တဲ့အခါမှာ single element ကို ပဲ mount လုပ်တာဖြစ်တဲ့အတွက်ကြောင့် container တစ်ခုတည်းမှာ ပဲ ထည့်သုံးပေးရတာဖြစ်ပါတယ်။

---

### How to work function in return Multi or More HTML Elements

```jsx
import React from "react";
import ReactDOM from "react-dom";

function Greeting() {
  return React.createElement(
    "div",
    {},
    React.createElement("h1", {}, "This is heading"),
    React.createElement("p", {}, "This is paragraph")
  );
}

ReactDOM.render(<Greeting />, document.getElementById("root"));
```

---

### JSX rules

1. always return single element
2. div /selection /article or Fragment
3. use camelCase for html Attribute
4. use className instead of class
5. close every element
6. formatting

---

### JSX-CSS and JSX-Javascript

#### CSS

```jsx
import "./index.css";

function Card() {
  return <main className="css-classname"></main>;
}
```

react မှာ css ကို external style နဲ့သုံးချင်ရင် css file ကို `import` အရင် လုပ်ပေးရတယ်။ ပြီးမှ ကိုယ်သုံးချင်တဲ့ classname ကို `className="__"` နဲ့ သုံးပေးရပါတယ်။

---

#### JSX-CSS

##### Inline Style

```jsx
function Card() {
  return <h1 style={{ marginTop: "1rem", textAlign: "center" }}>Card Title</h1>;
}
```

react မှာ css properties တွေကို camelCase နဲ့ သုံးရပါတယ်။ အထက်က ရေးတဲ့ပုံသည် inline style ဖြစ်ပါတယ်။

##### Internal Style

```jsx
function Card() {
  const styles = {
    title: {
      fontSize: 18,
      color: "#999",
      fontWeight: 900,
    },
  };

  return <h1 style={styles.title}>Card Title</h1>;
}
```

Internal Style ကို ရေးလျှင် **json format** ဖြစ်တဲ့အတွက် ပြန်ခေါ်သုံးခြင်လျှင် object ထဲက value တွေကို ပြန်ခေါ်သုံးသလို **keyname** နဲ့ ပြန်ခေါ်သုံးပေးရပါတယ်။

---

#### JSX-JavaScript

```jsx
const title = "Hello World";

function Card() {
  return <h1>{title}</h1>;
}
```

react မှာ JavaScript code တွေကို document မှာဖော်ပြချင်လျှင် tag or element တစ်ခုရဲ့ အထဲမှာ `{}` နဲ့ ရေးပါတယ်။

---

### React Props

#### Passing Data

```jsx
function CardList() {
  return (
    <main>
      <Card title="card title" text="hello world" />
    </main>
  );
}

function Card(props) {
  return (
    <div>
      <h1>{props.title}</h1>
      <p>{props.text}</p>
    </div>
  );
}
```

- **important**
  - Props သည် Parent to Child ကိုပဲ data passing လုပ်လို့ရပါတယ်။ Props သည် **json format** နဲ့ data ပေးပို့တဲ့ အတွက်ကြောင့် ပြန်ခေါ်သုံးတဲ့အခါမှာ `props.title` ဆိုပြီး ခေါ်သုံးပေးရပါတယ်။

---

#### How to passing object data using props

```jsx
const cardOne = {
  image: "https://via.placeholder.com/150/92c952",
  title: "Card Title",
  description: "card description",
};

const cardTwo = {
  image: "https://via.placeholder.com/150/92c952",
  title: "Card Title Two",
  description: "card two description",
};

function CardList() {
  return (
    <main className="card-list">
      <Card
        image={cardOne.image}
        title={cardOne.title}
        description={cardOne.description}
      />
      <Card
        image={cardTwo.image}
        title={cardTwo.title}
        description={cardTwo.description}
      />
    </main>
  );
}

function Card(props) {
  return (
    <section className="card">
      <img src={props.image} alt="card-img" />
      <h1>{props.title}</h1>
      <p>{props.description}</p>
    </section>
  );
}
```

---

#### Destructuring Props

##### First Syntax

```jsx
function Card(props) {
  const { image, title, description } = props;

  return (
    <div>
      <img src={image} alt="card-img" />
      <h1>{title}</h1>
      <p>{description}</p>
    </div>
  );
}
```

##### Second Syntax

```jsx
function Card({ image, title, description }) {
  return (
    <div>
      <img src={image} alt="card-img" />
      <h1>{title}</h1>
      <p>{description}</p>
    </div>
  );
}
```

Props ကို **Destructuring** လုပ်ပြီး ခေါ်သုံးလျှင် props keyword ပြန်ခေါ်စရာမလိုပါဘူး။ props ထဲမှာပါလာတဲ့ value တွေကိုပဲ ခေါ်သုံးပေးရမှာ ဖြစ်ပါတယ်။

---

#### Props Children

```jsx
function CardList() {
  return (
    <main>
      <Card>
        <p>hello world</p>
      </Card>
    </main>
  );
}

function Card({ children }) {
  return <h1>{children}</h1>;
}
```

Props Children တွေကို ခေါ်သုံးတဲ့အခါမှာ object destructuring ဖြစ်တဲ့ `{}` ထဲမှာ **children** ဆိုတဲ့ keyword ကို ခေါ်သုံးရပါမယ်။

---

#### Rendering Item

```jsx
const cards = [
  {
    image: "https://via.placeholder.com/150/92c952",
    title: "Card Title",
    description: "card description",
  },
  {
    image: "https://via.placeholder.com/150/92c952",
    title: "Card Title Two",
    description: "card two description",
  },
];

function CardList() {
  return (
    <main className="card-list">
      {cards.map((card, index) => {
        return (
          <Card
            key={index}
            image={card.image}
            title={card.title}
            description={card.description}
          />
        );
      })}
    </main>
  );
}

function Card({ image, title, description, children }) {
  return (
    <section className="card">
      <img src={image} alt="card-img" />
      <h1>{title}</h1>
      <p>{description}</p>
    </section>
  );
}
```

Components တွေကို rendering လုပ်တဲ့အခါမှာ map methods ကိုသုံးပြီး looping လုပ်ပြီးတော့ ထုတ်ပါတယ်။
သတိထားရမယ့်တစ်ချက်ကတော့ rendering လုပ်မယ့် components မှာ key value ထည့်ပေးရမှာဖြစ်ပါတယ်။ key value သည် unique ဖြစ်ရမယ်။
object ထဲမှာ id ပါလျှင် id key ကိုယူလို့ရသလို မပါခဲ့လျှင်လည်း index number ကို ယူလို့ရပါတယ်။ နောက်တစ်နည်းကတော့ id ကို
Math methods ကို random number ထုတ်ပြီး မှတ်လို့လည်း ရပါတယ်။ ဥပမာ -

```javascript
const card = [
  {
    id: Math.random().toString(),
  },
  {
    id: Math.random().toString(),
  },
];
```

Rendering လုပ်ရချင်းသည် data တွေဘယ်လောက်ပဲများများ target data ကို looping လုပ်နေတဲ့ အတွက်ကြောင့် data ထပ်တိုးတာပဲ
ဖြစ်ဖြစ်၊ လျှော့သွားတဲ့ပဲ ဖြစ်ဖြစ်၊ update ဖြစ်နေချင်တဲ့အတွက်ကြောင့်ပဲ ဖြစ်ပါတယ်။

---

#### Spread Operator

```jsx
function CardList() {
  return (
    <main className="card-list">
      {cards.map((card, index) => {
        return <Card key={index} {...card} />;
      })}
    </main>
  );
}

function Card({ image, title, description }) {
  return (
    <section className="card">
      <img src={image} alt="card-img" />
      <h1>{title}</h1>
      <p>{description}</p>
    </section>
  );
}
```

Object ကို spread လုပ်လိုက်တဲ့အတွက်ကြောင့် props name declare လုပ်ပေးစရာမလိုတော့ပဲ child component မှာ တစ်ခါတည်း props
ကို destructuring လုပ်ပြီးလှမ်းခေါ်သုံးနိုင်ပါတယ်။

---

#### React Events

```jsx
function Card() {
  function clickHandler() {
    console.log("button is working");
  }

  return <button onClick={clickHandler}>Click Me</button>;
}
```

function ပြန်ခေါ်ရင် () ထည့်ရတယ်ဆိုပေမယ့် reactjs မှာတော့ () ထည့်လိုက်ရင် auto run သွားမှာဖြစ်ပါတယ်။ တကယ်လို့ function
မှာ () ထည့်ဖို့လိုလာခဲ့ရင် ယခုလိုရေးပါတယ်။

```jsx
function Card() {
  function clickHandler() {
    console.log("button is working");
  }

  return (
    <div>
      <button onClick={() => clickHandler()}>Click Me</button>
    </div>
  );
}
```

event object တိုင်းမှာ event တစ်ခုရှိနေပါတယ်။ ထို event ကို function မှာ parameter နဲ့ access လုပ်လို့ရပါတယ်။ ဥပမာ -

```javascript
function clickHandler(e) {
  console.log(e);
}
```

---

#### Import and Export Statement

Export လုပ်တဲ့ method နှစ်မျိုးရှိပါတယ်။

- First Method

```jsx
export const cards = [
  {
    image: "https://via.placeholder.com/150/92c952",
    title: "Card One",
    description: "card description",
  },
];
```

First Method ကို import လုပ်ချင်ရင်တော့

```javascript
import { cards } from "./cards";
```

First Method သည် name ကို export လုပ်တာဖြစ်လို့ name ကိုပြောင်းလဲလို့မရပါဘူး။ အဲ့ဒါကြောင့် ထို name အတိုင်းပြန်
ပေးရပါမယ်။ components name ကို ပြောင်းလဲချင်ရင်တော့

```javascript
import { cards as Cards } from "./cards";
```

- Second Method

```jsx
function Card({ image, title, description }) {
  function clickHandler() {
    console.log("Click is working");
  }

  return (
    <section className="card">
      <img
        onMouseOver={() => console.log("i am hover")}
        src={image}
        alt="card-img"
      />
      <h1>{title}</h1>
      <p>{description}</p>
      <button onClick={clickHandler}>Click Me</button>
    </section>
  );
}

export default Card;
```

Second Method ကတော့ components ကို default export လုပ်တာဖြစ်တဲ့အတွက်ကြောင့် import လုပ်တဲ့အခါမှာ name ကို
ကြိုက်တာပေးလို့ရပါတယ်။

```javascript
import CardComponent from "./Card";
```

File တစ်ခုတည်းမှာ component တစ်ခုထက်ပိုပြီး export လုပ်ချင်ရင်တော့

```javascript
export const data1 = [1, 2, 3, 4];
export const data2 = [5, 6, 7, 8];
export const data3 = [9, 10, 11, 12];
```

import လုပ်ချင်ရင်တော့

```javascript
import { data1, data2, data3 } from "./datas";
```

- **Important**
  - multi export လုပ်လျှင် export default နဲ့ ပေးလို့မရပါဘူး။
