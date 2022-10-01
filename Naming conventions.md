# Naming conventions

- Use **camelCase** formatting for most variable and function names. Such names begin with lowercase letter. If the name contains multiple words then, each subsequent word should begin with an uppercase letter. i.e. `let answerToUltimateQuestion = 42`
- Use uppercase names with underscores(SCREAMING_SNAKE_CASE) to represent constants i.e.`const INTEREST_RATE = 0.0525`

- Constants used to store functions should follow the the same rule as variable and function names: use camelCase for most functions and PascalCase for constructor function.

```jsx
const sayHi = function() {
	console.log("hi");
};

const Pet = function(name) {
	this.name = name;
};
```

- Names that follow the naming convention above are called Idiomatic names, names that sound natural to native speakers.