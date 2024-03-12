---
title: "Fetch API 111"
description: "Lorem ipsum dolor sit amet"
pubDate: "Jul 08 2023"
heroImage: "/rest-and-graphql/blog-placeholder-3.jpg"
---

### Using the Fetch API

##### Getting a resource

```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then((response) => response.json())
  .then((json) => console.log(json));
```

Output

```json
{
  "id": 1,
  "title": "...",
  "body": "...",
  "userId": 1
}
```

##### Listing all resources

```javascript
fetch("https://jsonplaceholder.typicode.com/posts")
  .then((response) => response.json())
  .then((json) => console.log(json));
```

Output

```json
[
  {
    "id": 1,
    "title": "...",
    "body": "...",
    "userId": 1
  },
  /** ... */
  {
    "id": 100,
    "title": "...",
    "body": "...",
    "userId": 1
  }
]
```

##### Creating a resource

```javascript
fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST",
  body: JSON.stringify({
    title: "foo",
    body: "bar",
    userId: 1,
  }),
  headers: {
    "Content-type": "application/json; charset=UTF-8",
  },
})
  .then((response) => response.json())
  .then((json) => console.log(json));
```

Output

```json
{
  "id": 101,
  "title": "foo",
  "body": "bar",
  "userId": 1
}
```

```bash
ngrok http 3000
```

```swift
import UIKit

class ViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()

        // Create a label
        let label = UILabel()
        label.translatesAutoresizingMaskIntoConstraints = false
        label.text = "Hello, World!"
        label.textAlignment = .center
        label.font = UIFont.systemFont(ofSize: 24)
        view.addSubview(label)

        // Add constraints to center the label
        NSLayoutConstraint.activate([
            label.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            label.centerYAnchor.constraint(equalTo: view.centerYAnchor)
        ])
    }
}

// Create the app's window and set the root view controller
let window = UIWindow(frame: UIScreen.main.bounds)
let viewController = ViewController()
window.rootViewController = viewController
window.makeKeyAndVisible()
```
