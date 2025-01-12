```javascript
// Get a copy of the canvas content element
let view = app.workspace.activeLeaf.view;
if (view.getViewType() !== "canvas") {
  throw new Error("The active view is not a canvas");
}
let content = view.contentEl.cloneNode(true);

// Remove the canvas background dots
content.querySelector(".canvas-background").remove();

// Remove the canvas UI controls
content.querySelector(".canvas-card-menu").remove();
content.querySelector(".canvas-controls").remove();

// Remove the canvas node labels (image filenames)
content.querySelectorAll(".canvas-node-label").forEach((el) => el.remove());

// Get all the CSS, except for print styles
// https://developer.mozilla.org/en-US/docs/Web/API/StyleSheetList#get_all_css_rules_for_the_document_using_array_methods
let allCSS = [...document.styleSheets]
  .map((styleSheet) =>
    [...styleSheet.cssRules]
      .map((rule) => rule.cssText)
      .filter((cssText) => !cssText.includes("@media print")) // No print styles
      .join("\n")
  )
  .join("\n");

// Global regex matches app:// followed by any characters except /
let pattern = /app:\/\/[^\/]*/g;

// Generate HTML & CSS. Remove any app:// prefixes from URLs.
let html = `
<!DOCTYPE HTML>
<html>
<head>
<style>
${allCSS}
/* Use exact colors for card backgrounds and bullets */
body { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
</style>
</head>
<body class="${document.querySelector("body").className}">
${content.outerHTML}
</body>
</html>`.replaceAll(pattern, "");

// Save html file
let filename = "canvas-export.html";
existingFile = app.vault.getAbstractFileByPath(filename);
if (existingFile) {
  app.vault.delete(existingFile);
}
app.vault.create(filename, html);

console.log("Open this file in your browser and print to PDF:");
console.log(`${app.vault.adapter.basePath}/${filename}`);
```