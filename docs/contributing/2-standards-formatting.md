# Standards and Formatting Guide

This guide outlines the standards to adhere to for page naming, directory structure, and other related items, along with guides on how to use the various markdown attributes and other MkDocs Material extensions we have enabled to enhance the documentation.

## Mandatory Standards

We try to keep as few mandatory standards as possible, but these items must be adhered to in order for our documentation to be maintainable.

### General Content

When creating content, remember to keep the target user in mind at all times, with a strong preference to Conductor level users. A significant (and growing) proportion of our user base do not understand software, nor a lot of electronics or embedded systems. Use terminology they are likely understand.

Most importantly, *keep pages concise, to the point, and avoid excess words or waffle*. Not only does this make the key messages hard to read, but maintaining lengthy pages that are a wall of text becomes onerous, daunting, and reduces the likelihood of keeping our documentation current.

### Page Naming and Titles

- All page names must be in lower case and use "-" instead of spaces where appropriate.
- If specific page ordering is required, simply preface with the appropriate page number eg. "1-standards-formatting.md".
- The page title is determined by the top level heading, see [Headings](#headings).

### Directory Structure

Note firstly that we use the [MkDocs Awesome Nav plugin](https://lukasgeiter.github.io/mkdocs-awesome-nav/) to control the menu structure, which uses a ".nav.yml" file in any directory where the default needs to be overridden.

The top level directories under the "docs" directory determine the tabs or horizontal menu items on the header bar, with the subsequent directories and files in each of these determining the menu on the left pane.

**Do not adjust the top level directories without consulting the DCC-EX Documenter team, as these fundamentally adjust the user experience.**

If a new top level directory is to be added, it needs to be added to the "/docs/.nav.yml" file in the appropriate order. Files and directories created within existing top level directories will automatically be added to the menus (see [Page Naming and Titles](#page-naming-and-titles) for page ordering).

## Page and Section Links

There are three types of links you can use:

- Section links - link to another section heading on the same page
- Document links - link to another document, or a section heading on another document
- External links - link to an external website

All internal links to other pages and sections should be relative, not absolute. We have enabled a setting to ensure links are relative to the "docs" directory, and enable permalinks for headings to support this.

External links must be absolute.

### Section Links

Links to sections on the same page should just use the permalink section heading name:

```markdown
[Link to this section](#page-and-section-links)
```

Results in: [Link to this section](#page-and-section-links)

### Document Links

```markdown
[Link to Contributing to Documentation Page](/contributing/1-contribute-docs.md)
```

Results in: [Link to Contributing to Documentation Page](/contributing/1-contribute-docs.md)

```markdown
[Link to How to Contribute Section](/contributing/1-contribute-docs.md#how-to-contribute)
```

Results in: [Link to How to Contribute Section](/contributing/1-contribute-docs.md#how-to-contribute)

### External Links

```markdown
[Link to Google Search](https://www.google.com)
```

Results in: [Link to Google Search](https://www.google.com)

## Search Links

**Chris to insert search link info here.**

## Headings

Headings are simply defined by one or more leading ``#``, noting you can only have one top level heading on a page, which is the page title.

The top level heading defines how the page appears in menus, so for this page this is the top level heading:

```markdown
# Standards and Formatting Guide
```

Further, this general section on "Headings" is a second level heading:

```markdown
## Headings
```

Following are how to define the lower level headings with a demo of each.

### Heading Level 3

```markdown
### Heading Level 3
```

#### Heading Level 4

```markdown
#### Heading Level 4
```

##### Heading Level 5

```markdown
##### Heading Level 5
```

## Code blocks

When including code blocks, be sure to include an appropriate language for syntax highlighting, and use triple backtick "`" characters to surround the code for highlighting.

For example:

````cpp
```cpp
TURNOUTL(id, address, "description")

TURNOUT(id, shortAddress, subAddress, "description")
```
````

Will render as:

```cpp
TURNOUTL(id, address, "description")

TURNOUT(id, shortAddress, subAddress, "description")
```

For EXRAIL and general configuration file code blocks (eg. config.h, myAutomation.h), "cpp" is as good as any, and for any others use an appropriate language specifier.

If appropriate, line numbers can also be displayed by appending ``linenums="X"`` to the language, where "X" is the starting line number:

````cpp
```cpp linenums="20"
TURNOUTL(id, address, "description")

TURNOUT(id, shortAddress, subAddress, "description")
```
````

Will render as:

```cpp linenums="20"
TURNOUTL(id, address, "description")

TURNOUT(id, shortAddress, subAddress, "description")
```

This is a nonsense C++ code block generated by Gemini to demonstrate the full syntax highlighting:

```cpp
#include <iostream>  // Standard I/O library
#include <vector>    // For dynamic arrays
#include <string>    // For string manipulation
#include <map>       // For key-value pairs

// A simple namespace to organize code
namespace MyLibrary {

const double PI_VALUE = 3.1415926535; // A global constant

/**
 * @brief Represents a generic item with properties.
 * This is a multi-line comment to test comment colors.
 */
class GenericItem {
private:
    std::string itemName;
    int itemId;
    double itemPrice;
    bool isAvailable;

public:
    // Constructor with default values
    GenericItem(const std::string& name = "Default Item", int id = 0, double price = 0.0, bool available = true)
        : itemName(name), itemId(id), itemPrice(price), isAvailable(available) {}

    // Member function to display item details
    void displayDetails() const {
        std::cout << "Item Name: " << itemName << std::endl;
        std::cout << "Item ID: " << itemId << std::endl;
        std::cout << "Price: $" << itemPrice << std::endl;
        std::cout << "Available: " << (isAvailable ? "Yes" : "No") << std::endl;
    }

    // Getter for itemPrice
    double getPrice() const {
        return itemPrice;
    }

    // Setter for itemPrice (with a simple check)
    void setPrice(double newPrice) {
        if (newPrice >= 0.0) {
            this->itemPrice = newPrice;
        } else {
            std::cerr << "Warning: Price cannot be negative." << std::endl;
        }
    }
}; // Don't forget the semicolon after class definition!

// Template function to find the maximum of two values
template <typename T>
T findMax(T a, T b) {
    return (a > b) ? a : b; // Ternary operator test
}

} // end namespace MyLibrary

// Main function - entry point of the program
int main() {
    using namespace MyLibrary; // Use MyLibrary namespace

    // Create instances of GenericItem
    GenericItem item1("Laptop", 101, 1200.50, true);
    GenericItem* item2 = new GenericItem("Mouse", 202, 25.99, false); // Using 'new'

    // Display details using a loop
    std::vector<GenericItem> inventory;
    inventory.push_back(item1);
    inventory.push_back(*item2);

    std::cout << "--- Inventory Details ---" << std::endl;
    for (const auto& item : inventory) { // Range-based for loop
        item.displayDetails();
        std::cout << "-------------------------" << std::endl;
    }

    // Test the template function
    int maxInt = findMax(10, 20);
    double maxDouble = findMax(PI_VALUE, item2->getPrice()); // Accessing member via pointer

    std::cout << "Maximum integer: " << maxInt << std::endl;
    std::cout << "Maximum double: " << maxDouble << std::endl;

    // Exception handling test
    try {
        if (item1.getPrice() < 1.0) {
            throw "Price too low!"; // Throwing a string literal
        }
        item1.setPrice(1500.00); // Change price
    } catch (const char* msg) { // Catching a C-style string
        std::cerr << "Error: " << msg << std::endl;
    }

    // Clean up dynamic memory
    delete item2; // Using 'delete'
    item2 = nullptr; // Best practice to nullify pointer after delete

    // Return 0 for successful execution (integer literal)
    return 0;
}
```
