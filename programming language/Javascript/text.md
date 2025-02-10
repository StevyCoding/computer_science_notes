

# sort algorithm 


```dataviewjs
const container = this.container;
container.innerHTML = ''; // Clear previous content

// Create Textarea
const textarea = document.createElement("textarea");
textarea.rows = 5;
textarea.cols = 40;
textarea.placeholder = "Enter your data here, each value on a new line...";
container.appendChild(textarea);

// Create Button
const sortButton = document.createElement("button");
sortButton.innerText = "Sort Data";
container.appendChild(sortButton);

// Create Output Div
const outputDiv = document.createElement("div");
outputDiv.style.marginTop = "10px";
container.appendChild(outputDiv);

// Sort Function
sortButton.addEventListener("click", () => {
    let data = textarea.value.split("\n").map(line => line.trim()).filter(line => line !== "");
    
    // Sort by first letter
    data.sort((a, b) => a[0].localeCompare(b[0]));
    
    // Display sorted results
    outputDiv.innerHTML = "<strong>Sorted Data:</strong><br>" + data.join("<br>");
});

```

