# Coderbyte
Codebyte | Node.js | Backend Developer Assessment 

##Simple password

```
function doesContainCapitalLetter(str) {
  return str.split('').some(char => (char === char.toUpperCase()));
}


function doesContainDigitCharacter(str) {
  return (/\d/).test(str);
}


function doesContainPunctuationMark(str) {
  return (/[{(<!@#$%^&*_+-=;':'".,">)}]/).test(str);
}


function doesNotContainPasswordLiterally(str) {
  return !(/password/i).test(str);
}

function doesHaveCorrectLength(str) {
  return ((str.length >= 8) && (str.length <= 30));
}


function SimplePassword(str) {

  let isValid = doesHaveCorrectLength(str);

  isValid = isValid && doesNotContainPasswordLiterally(str);
  isValid = isValid && doesContainPunctuationMark(str);
  isValid = isValid && doesContainDigitCharacter(str);
  isValid = isValid && doesContainCapitalLetter(str);

  return isValid;
}
console.log(SimplePassword(readline()));
```

##star rating

```
unction StarRating(str) {

var flag = '';
var str1 = '';
var num = Number(str);
var int_num = Math.floor(num);
var frac = num - int_num;
if(frac!=0)
  var int_num_roof= (int_num+1);
else
  var int_num_roof = int_num;

while(int_num > 0){
  str1 += 'full ';//*int_num;
  int_num = int_num - 1;
}

if (frac<=0.5 && frac >0)
  str1 += 'half ';


if(frac<1 && frac >0.5)
  str1 += 'full ';

 
while ((5 - int_num_roof)  > 0){
  str1 +='empty ';
  int_num_roof++;
  if(int_num_roof == 5){
    str += 'empty';
    break;
  }
  }

return str1;
}

 

console.log(StarRating(readline()));


```

##node.js Print files

```
const fs = require('fs');

const exec = require('child_process').exec; 


// create file called newfile.txt

var data = 'THIS   I S   T H E   R A N D O M   D A T A';

fs.writeFile('newfile.txt', data, (err) => {
    // throws an error, you could also catch it here
    
    if (err) throw err;

        
});





exec('ls', (error, stdout, stderr) => {
  if (error) {

          console.error(`exec error: ${error}`);

    return;
  }
 
  //console.log(`${stdout}`)
  //console.log(stdout.length);
  var res = stdout.split("\n");
  // 
  res.pop();

  //console.log(typeof res.join());
//console.log("main.js, newfile.txt");


  
 console.log(res.join().split(',').join(', '));
  
});
```


##Node.js Age Counting

```
const https = require('https');

https.get('https://coderbyte.com/api/challenges/json/age-counting', (resp) => {
  
  let {statusCode} = resp
  let contentType = resp.headers['content-type']
  resp.setEncoding('utf-8')
  let data = '';

  // parse json data here...
  resp.on('data', (d) => {
    data += [d]
  })

    resp.on('end', () => {
    let parsedData = data.split(",")
    .filter(data =>!data.indexOf(" age="))
    .map(data => data.replace(" age=",""))
    .map(data => parseInt(data))
    .filter(data => {
     return (data >= 50);
    }).length
    console.log(parsedData);
  })
  resp.on("error", (e) => {
    console.log("error", e)
  })

  //console.log(resp);

});

```

