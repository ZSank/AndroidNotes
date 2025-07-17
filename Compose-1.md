# Compose

## Introduction
- Jetpack compose is used to show UI in Android app. It replaced XML layout.
- Jetpack compose is interoperable with XML. Compose can be used inside xml and xml can be used inside compose.
- Compose maker writing UI easier, more reusable.

### What you will learn
- Text, Column, Row composable. 

### About UI
- Whatever we see on the screen is called a UI. The button, text, animation, images, calendar.
- Everything is a separate elements. 
- Complex UI will be build by grouping together basic UI elements. 

### Jetpack Compose
- It is a modern UI toolkit for Building Android UI. 

### Composable Functions
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

### Column Composable
- 

### Button

### Image

## Creating a simple App

### Steps
1. Create a new composable. 
2. Add text composable. 
3. Increase font size using `fontSize` parameter
4. Add few more text. 
5. Arrange them in a column. 
