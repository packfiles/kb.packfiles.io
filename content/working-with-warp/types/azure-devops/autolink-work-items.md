# /autolink-work-items

## Description

Configures Autolink References in the destination GitHub repository so that references to Azure Boards work items become clickable hyperlinks.

[View in Knowledge Base](https://kb.warp.io/warp/commands/azure-devops/autolink-work-items)

## Example

```
/autolink-work-items
```

## Authorization

* Not required.

## Code Examples

### TypeScript

```typescript
interface WorkItem {
    id: number;
    title: string;
}

function autolinkWorkItems(items: WorkItem[]) {
    items.forEach(item => {
        console.log(`Configuring Autolink for Work Item: ${item.id} - ${item.title}`);
    });
}

const workItems: WorkItem[] = [
    { id: 1, title: "Fix bug in login" },
    { id: 2, title: "Add new feature" }
];

autolinkWorkItems(workItems);
```

### JavaScript

```javascript
function autolinkWorkItems(items) {
    items.forEach(item => {
        console.log(`Configuring Autolink for Work Item: ${item.id} - ${item.title}`);
    });
}

const workItems = [
    { id: 1, title: "Fix bug in login" },
    { id: 2, title: "Add new feature" }
];

autolinkWorkItems(workItems);
```

### Ruby

```ruby
WorkItem = Struct.new(:id, :title)

def autolink_work_items(items)
  items.each do |item|
    puts "Configuring Autolink for Work Item: #{item.id} - #{item.title}"
  end
end

work_items = [
  WorkItem.new(1, "Fix bug in login"),
  WorkItem.new(2, "Add new feature")
]

autolink_work_items(work_items)
```

### Go

```go
package main

import "fmt"

type WorkItem struct {
    ID    int
    Title string
}

func autolinkWorkItems(items []WorkItem) {
    for _, item := range items {
        fmt.Printf("Configuring Autolink for Work Item: %d - %s\n", item.ID, item.Title)
    }
}

func main() {
    workItems := []WorkItem{
        {ID: 1, Title: "Fix bug in login"},
        {ID: 2, Title: "Add new feature"},
    }

    autolinkWorkItems(workItems)
}
```

### Rust

```rust
struct WorkItem {
    id: u32,
    title: String,
}

fn autolink_work_items(items: Vec<WorkItem>) {
    for item in items {
        println!("Configuring Autolink for Work Item: {} - {}", item.id, item.title);
    }
}

fn main() {
    let work_items = vec![
        WorkItem { id: 1, title: String::from("Fix bug in login") },
        WorkItem { id: 2, title: String::from("Add new feature") },
    ];

    autolink_work_items(work_items);
}
```
