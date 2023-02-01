# OTF studio locations

List of all OTF studio locations in JSON format.

## How to extract?
* Go to [OTF studio locations page]([url](https://www.orangetheory.com/en-us/studio-location))
* Run the following in Javascript console:
```typescript
const output = [];

document.querySelectorAll('.studios-cl-wrapper [role="listitem"] .w-embed').forEach((embed) => {
  const link = embed.querySelector('a.global-studio-link-item');
  const name = link.querySelector('div:first-of-type').textContent.trim();
  const address = link.querySelector('div:nth-of-type(2)').textContent.trim();
  const linkHref = link.getAttribute('href');

  output.push({
    name,
    address,
    link: linkHref
  });
});


function dedupeArray(array) {
  return Array.from(new Set(array.map(JSON.stringify))).map(JSON.parse);
}

JSON.stringify(dedupeArray(output));
```
