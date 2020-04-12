## Meme Generator

Insert in the web page on top left corner a meme

```javascript
//todo: build a content with your favorite characters showing good stuff for you

// collection pictures
var newBlock = document.createElement('aside');
newBlock.setAttribute('id', 'MainMeme');
newBlock.setAttribute(
  'style',
  'position:absolute;border: 1px solid green;width: 20%;top:0;left:0;text-align: center;z-index: 99999;background: gray;',
);

//child element
var url =
  'https://media1.tenor.com/images/231c3ab28b2f1472c2c8f4010e34602a/tenor.gif';
//var url = 'https://envylabs.com/000097d492fad711261c7873c34080ca.svg';
// var url = "https://i.imgur.com/71YAt0R.jpg";
var newBlockImagine = document.createElement('img');
newBlockImagine.setAttribute('src', url);

var newBlockTitle = document.createElement('h3');
newBlockTitle.setAttribute('id', 'TitleMeme');
newBlockTitle.innerText = 'Main Meme Title';

//appendChild to the node

newBlock.appendChild(newBlockTitle);
newBlock.appendChild(newBlockImagine);

document.body.appendChild(newBlock);
```
