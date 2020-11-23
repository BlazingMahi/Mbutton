# BlazingMahi Mbutton
This is a customized button implementation for [Blazor](https://blazor.net) and Razor Components applications. It provides the ability to disable the button when clicked.

![Screenshot of component in action](screenshot.gif)

## Getting Started

You can install the package via the NuGet package manager just search for BlazingMahi. You can also install via powershell using the following command.

```powershell
Install-Package BlazingMahi.Mbutton
```

### Add Imports
Add the following to your _Imports.razor or to your razor page files.
```csharp
@using BlazingMahi.Mbutton
```
### Add Mbutton Component
Mbutton is configured using parameters on the `<Mbutton></Mbutton>` component. The following options are available.

- Class
- OnClick
- DisableOnClick (Default: false)
- Type (Default: button )
- SpinnerOnDisabled
- SpinnerClass (Default: "spinner-border spinner-border-sm")

Example: add Bootstrap button classes, OnClick event and set the disable to `true`

```html
<Mbutton Class="btn btn-primary" OnClick="IncrementCount" DisableOnClick="true">Click Me</Mbutton>

<p>Current count: @currentCount</p>

@code {
    private int currentCount = 0;

    private async Task IncrementCount()
    {
        currentCount++;
    }
}

```
The above example will disable the button when clicked and then call the `IncrementCount()` Method

### Re-enable the button after a Task is completed.
Using the component reference you have access to two methods. `EnableButton()` and `DisableButton()`
![Screenshot of component in action](countdown.gif)
```html
<Mbutton Class="btn btn-primary" OnClick="IncrementCount" DisableOnClick="true" @ref="mbutton">Click Me</Mbutton>

@code {
    private int currentCount = 0;
    Mbutton mbutton;

    private async Task IncrementCount()
    {
        await Task.Delay(3000);
        currentCount++;
        mbutton.EnableButton();
    }
}

```
### Add Bootrap Spinner when disabled.
![Screenshot of component in action](spinner.gif)

You can add a Bootstap spinner to the button when the button is disabled on click.

-  https://getbootstrap.com/docs/4.5/components/spinners/#buttons

```html
<Mbutton Class="btn btn-primary" 
         OnClick="IncrementCount" 
         DisableOnClick="true" 
         SpinnerOnDisabled="true">Click Me</Mbutton>

<p>Current count: @currentCount</p>

@code {
    private int currentCount = 0;  
    private void IncrementCount()
    {        
        currentCount++;       
    }   
}

```
#### You can also overide the default Spinner class
Override with other Bootstrap spinner properties
https://getbootstrap.com/docs/4.5/components/spinners/#growing-spinner

![Screenshot of component in action](spinner-custom.gif)


```html
<Mbutton Class="btn btn-primary" 
         OnClick="IncrementCount" 
         DisableOnClick="true" 
         SpinnerOnDisabled="true" 
         SpinnerClass="spinner-grow spinner-grow-sm">Click Me</Mbutton>
```


