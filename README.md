# Blazor WebAssembly App Template with Bootstrap Navbar

This is the _Blazor Webassembly_ Visual Studio template with the following changes:

1. **Bootstrap** as client library;
2. **jQuery** as client library;
3. Bootstrap _Navbar_ instead of side navigation (sidebar) panel.

## Collapse Breakpoint

Collapse breakpoint is set to _576px_. Change this behavior by changing the `<nav>`'s `navbar-expand-sm`
class to the appropriate class.

## Auto-collapse on Click

Navbar auto-collapse on click is implemented by setting a jQuery `on` event handler in _index.html_:

```js
        window.initNavMenu =
            () =>
                $('.navbar-nav > li a:not("[data-toggle]")').on(
                    'click',
                    () => $('.navbar-collapse').collapse('hide')
                );
```

The jQuery `$(document).ready()` event is **not** fired on SPAs. So the menu item click handler
is set in the NavMenu's `OnAfterRender` method:

```csharp
    protected override async void OnAfterRender(bool firstRender)
    {
        await JSRuntime.InvokeVoidAsync("initNavMenu");
        base.OnAfterRender(firstRender);
    }
```

## Links

[Bootstap Navbar Docs](https://getbootstrap.com/docs/4.5/components/navbar/)

[ASP.NET Core Blazor](https://docs.microsoft.com/en-us/aspnet/core/blazor/?view=aspnetcore-3.1)
