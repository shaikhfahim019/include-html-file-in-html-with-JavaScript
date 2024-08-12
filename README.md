Include html file in html with javascript and include one HTML page within another HTML, you have a few options depending on the context and the functionality you need.  Here’s how you can do it:


### 1. **Using `<iframe>`**

The `<iframe>` element is used to embed another HTML document within the current document. This method is simple and straightforward.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Parent Page</title>
    <style>
        iframe {
            width: 100%;
            height: 500px;
            border: none;
        }
    </style>
</head>
<body>
    <h1>Parent Page</h1>
    <iframe src="child.html" title="Embedded Page"></iframe>
</body>
</html>
```

### 2. **Using `<object>`**

The `<object>` tag can also be used to include another HTML page. This method can handle various types of embedded content.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Parent Page</title>
    <style>
        object {
            width: 100%;
            height: 500px;
        }
    </style>
</head>
<body>
    <h1>Parent Page</h1>
    <object data="child.html" type="text/html"></object>
</body>
</html>
```

### 3. **Using Server-Side Includes (SSI)**

If you're working on a server that supports Server-Side Includes, you can use the `<!--#include file="filename.html" -->` directive to include another HTML file.

**Example (`parent.html`):**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Parent Page</title>
</head>
<body>
    <h1>Parent Page</h1>
    <!--#include file="child.html" -->
</body>
</html>
```

**Note:** SSI requires server-side configuration and may not work on all servers.

### 4. **Using JavaScript (AJAX)**

You can use JavaScript to load and insert the content of one HTML file into another dynamically. This method is useful for single-page applications or dynamic content loading.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Parent Page</title>
    <style>
        #content {
            width: 100%;
            height: auto;
        }
    </style>
    <script>
        function loadContent() {
            fetch('child.html')
                .then(response => response.text())
                .then(data => document.getElementById('content').innerHTML = data);
        }
        window.onload = loadContent;
    </script>
</head>
<body>
    <h1>Parent Page</h1>
    <div id="content">
        <!-- Content from child.html will be loaded here -->
    </div>
</body>
</html>
```

**Note:** This method requires the server to support CORS (Cross-Origin Resource Sharing) if the files are on different domains.

Choose the method that best fits your use case and the capabilities of your server or environment.