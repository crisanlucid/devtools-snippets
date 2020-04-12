### EasterEgg - 2020 Google.com

Navigate to google.com.  Click **3x times** over google logo, and will appear an input with a **password** and a **questions box**.
Click the **Question box** where will appear a Dialog where to put the password. 
Correct password will lead to a new Dialog with message **Congrats you found the Easter Egg!**

```javascript
function initEasterEgg() {
  var newScript = document.createElement('script');
  newScript.setAttribute(
    'src',
    'https://cdnjs.cloudflare.com/ajax/libs/sweetalert/1.1.3/sweetalert-dev.min.js',
  );
  var newCSS = document.createElement('link');
  newCSS.setAttribute(
    'href',
    'https://cdnjs.cloudflare.com/ajax/libs/sweetalert/1.1.3/sweetalert.min.css',
  );
  newCSS.setAttribute('rel', 'stylesheet');

  document.body.appendChild(newScript);
  document.body.appendChild(newCSS);

  var createPasswordForm = () => {
    var password = 'XSDSDS';
    var newBlock = document.createElement('div');
    newBlock.setAttribute('id', 'PasswordForm');
    newBlock.setAttribute(
      'style',
      'position:absolute;border: 3px solid green;width: 20%;top: 0;left: 40%;text-align: center;z-index: 99999;background: gray;padding: 5px;',
    );
    var input = document.createElement('input');
    input.setAttribute('name', 'password');
    input.setAttribute('type', 'text');
    input.setAttribute('disabled', 'disabled');
    input.setAttribute('id', 'password');
    input.value = password;
    newBlock.appendChild(input);
    document.body.appendChild(newBlock);

    localStorage.setItem('easterEgg', password);
  };

  var createMisteryBox = () => {
    var newBlock = document.createElement('div');
    newBlock.setAttribute('id', 'MagicBox');
    newBlock.setAttribute(
      'style',
      'position:absolute;border: 4px solid #070000;width: 80px;top: 30vh;left: 47%;text-align: center;z-index: 99999;background: #F88D2E;box-shadow: inset -4px -4px 0 #965117, inset 4px 4px 0 #FAB89B;height: 80px;',
    );

    //child elems
    var urlSvg =
      'https://uglyduck.ca/public/images/mario-block-question-mark.svg';
    var newBlockImagine = document.createElement('span');
    newBlockImagine.setAttribute(
      'style',
      'display: block;height: 100%;position: relative;width: 100%;background-image:url(https://uglyduck.ca/public/images/mario-block-question-mark.svg);background-position: center;background-repeat: no-repeat;background-size: 40px;',
    );

    newBlock.appendChild(newBlockImagine);
    document.body.appendChild(newBlock);
  };

  //listen the logo and click 3x times
  var counter = 0;
  var logo = document.querySelector('[alt="Google"]');

  if (!logo) return;
  logo.addEventListener('click', (e) => {
    counter++;

    if (counter === 3) {
      //get a input text password
      createPasswordForm();

      //a box in the middle of page
      createMisteryBox();

      var button = document.querySelector('#MagicBox');

      button.addEventListener('click', (event) => {
        //modal where to put the password
        var getValue = prompt('Insert the password!');

        if (localStorage.getItem('easterEgg') === getValue) {
          //congrats with icon easter egg message
          swal('Congrats!', 'You won an Easter Egg!', 'success');
        } else {
          alert('GAME OVER!!');
        }
      });
    }
  });
}

initEasterEgg();
```
