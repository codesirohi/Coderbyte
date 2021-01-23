# Coderbyte
Codebyte | Node.js | Backend Developer Assessment 


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
