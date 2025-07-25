# Compose Basics


> In Android studio, enable `add unambiguous imports on fly`
### Resources
- [Get started with Jetpack Compose  |  Android Developers](https://developer.android.com/develop/ui/compose/documentation)
- Repo [Link](https://github.com/ZSank/IntroCard)
### Introduction
- Jetpack compose is used to show UI in Android app. It replaced XML layout.
- Jetpack compose is interoperable with XML. Compose can be used inside xml and xml can be used inside compose.
- Compose maker writing UI easier, more reusable.
### About UI
- Whatever we see on the screen is called a UI. The button, text, animation, images, calendar.
- Everything is a separate elements. 
- Complex UI will be build by grouping together basic UI elements. 

### Composable Functions Introduction
- It is a function with `@Composable` annotation. 
- This annotation makes it participate in the UI building process. This shown on the screen. 
- Basic compose functions. 
    ``` kotlin
    @Composable
    fun MyTextUI() {
        Text("Hello world")
    }
    ```
- Compose Function with parameter
    ``` kotlin
    @Composable
    fun MyTextUI(text: String) {
        Text(text)
    }
    ```
- Previewing composable with `@Preview` annotation
    ``` kotlin
    @Preview
    @Composable
    fun MyTextUI(text: String) {
        Text(text)
    }
    ```
- Preview annotation with parameters
    ``` kotlin
    @Preview(showBackground = true, showSystemUI = true, name = "TextPreview")
    @Composable
    fun MyTextUI(text: String) {
        Text(text)
    }
    ```
- Rules about naming composable
    - Must start with capital letter. 

## Basic composable
### Text Composable
- Text composable is used to show text. 
- It has many properties like `fontSize`, `fontStyle`, `color`, `maxLines` etc.
- Click `Ctrl + B`, to check the implementation and the properties of inbuilt code. 
- `sp` is used for font size. 
- `dp` is used for all other size in compose
- `textAlign`
    - Usage: `textAlign = TextAlign.Center`
    - Available `textAlign` options: `Left, Right, Center, Justify, Start, End`
- `lineHeight`: Add in `dp`

### Column Composable
- Introduction
    - Column is a simple composable. 
    - Child composable are placed inside it's body. 
    - It is used to arrange the children composable in a single column. 
    - It is like stacking blocks from top to bottom.
- Simple column code
    ``` kotlin
    @Composable
    fun MyComp() {
        Column() {
            Text("Enter Name")
            Text("Enter Number")
        }
    }
    ```
- Alignment
    - Column composable constructor takes modifier, `verticalArrangement`, `horizontalAlignment`, content. 
- `verticalArrangement`
- `horizontalAlignment`
- `padding`
    - Padding is spacing
    - simple padding
        ```kotlin
        Column(
            modifier = modifier.padding(10.dp)
        )
        ```
- Applications of Column
    - Use a Column when you want to:
    - Stack things vertically
    - Keep UI elements one below the other
    - Organize your layout in a top-down manner
      
### Row Composable
- Introduction
    - Similar to column composable, row composable functions the same. 
    - Key difference is, it arranges the children in a single row. 

### Box Composable
- Later

### Button Composable
- Later
### Image Composable
- Basic code
    ``` kotlin
    val image = painterResource(R.drawable.my_image)
    Image (
        painter = image,
        contentDescription = null
    )
    ```
- `contentScale = ContentScale.Crop, alpha = 0.8F`

### Modifier
``` kotlin
modifier = Modifier.background(color = Color.Green)
Modifer.fillMaxWidth().fillMaxHeight().fillMaxSize()
.padding(top= 5.dp).padding(all = 10.dp)

```

### Arrangement
- https://developer.android.com/reference/kotlin/androidx/compose/foundation/layout/Arrangement
### Show Compose in the App
- Add the composable in the `setContent{}` in the `onCreate`
- Code
``` kotlin
class MainActivity : ComponentActivity() {  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        enableEdgeToEdge()  
        setContent {  
            MyName()  
        }  
    }  
}
```
## Creating a simple App
### Steps
1. Create a new composable. 
2. Add text composable. 
3. Increase font size using `fontSize` parameter
4. Add few more text. 
5. Arrange them in a column. 


## Adding Image
1. Add the Image using resources tab. 
2. Image composable, refer the imported image. 
3. Do arrangements. 


## Adding Button and Lists data

### Button Composable
1. A **Button** is something the user can **tap or click** to make something happen.
2. In Compose, we use the `Button` composable to create it.
3. Basic button
    ``` kotlin
    @Composable
    fun MyScreen() {
        Button(onClick = { 
            // This code runs when the button is clicked
            println("Button was clicked!")
        }) {
            Text("Click Me")
        }
    }
    
    ```

### State in compose
1. Intro
    1. State means remembering information in your app.
    2. For example, if a user clicks a button, the app needs to remember how many times it was clicked.
    3. Without state, the app forgets everything each time it refreshes the screen.

2. Example without state (doesn't work correctly):
    ```kotlin
    @Composable
    fun CounterWithoutState() {
        var count = 0
    
        Button(onClick = {
            count++
        }) {
            Text("Count: $count")
        }
    }
    ```

    1. This code sets `count` to 0 every time, so the number never increases.
    2. Thus this implementation is incorrect. 
    3. Never use simple variable in composable, for values that will change. 

3. Working example using state:
    ```kotlin
    @Composable
    fun CounterWithState() {
        var count by remember { mutableStateOf(0) }
    
        Button(onClick = {
            count++
        }) {
            Text("Count: $count")
        }
    }
    ```
    1. `mutableStateOf(0)` creates a value that can change.
    2. `remember` makes sure the value is not lost when the screen updates.
    3. When `count` changes, Compose updates the screen to match the new value.

5. Another example with text input:
    ```kotlin
    @Composable
    fun NameInput() {
        var name by remember { mutableStateOf("") }
    
        Column {
            TextField(
                value = name,
                onValueChange = { newText -> name = newText },
                label = { Text("Enter your name") }
            )
            Text("Hello, $name!")
        }
    }
    ```
    1. `name` holds the user's typed input.
    2. The screen updates automatically as the user types.
6. Summary:
    1. State holds values that the UI needs to remember.
    2. `mutableStateOf` creates state.
    3. `remember` keeps the value safe during screen updates.
    4. Changing the state automatically refreshes the UI.


### Lazy Column Composable
1. Intro
    1. A `LazyColumn` is like a `Column`, **but it's optimized for long lists**.
    2. Instead of building **all items at once**, it builds only the ones **that are visible** on the screen. This makes it **faster and uses less memory**.
2. Usage of lazy column
    1. You have a list of items (names, messages, products, etc.)
    2. The list might be long
    3. You want better performance
3. Simple Example
    ``` kotlin
    @Composable
    fun MyLazyList() {
        LazyColumn {
            item {
                Text("Single item at the top")
            }
    
            items(10) { index ->
                Text("Item #$index")
            }
        }
    }
    
    ```
4. Other without lazyColumn (Not best practice)
    ``` kotlin
    @Composable
    fun ScrollableColumnList() {
        // Remember scroll state
        val scrollState = rememberScrollState()
    
        Column(
            modifier = Modifier
                .fillMaxSize()
                .verticalScroll(scrollState)  // Make it scrollable
                .padding(16.dp)
        ) {
            for (i in 1..100) {
                Text(
                    text = "Item #$i",
                    modifier = Modifier.padding(vertical = 8.dp)
                )
            }
        }
    }
    ```