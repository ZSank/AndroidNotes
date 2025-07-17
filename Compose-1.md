# Compose

## Introduction
- Jetpack compose is used to show UI in Android app. It replaced XML layout.
- Jetpack compose is interoperable with XML. Compose can be used inside xml and xml can be used inside compose.
- Compose maker writing UI easier, more reusable.

## Simple App with Compose
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