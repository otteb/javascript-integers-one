# javascript-integers-one

*this is a README file of the code. You can test the code below by copying and pasting the code into repl.it.com*

Directions:

Divisors of 42 are : 1, 2, 3, 6, 7, 14, 21, 42. These divisors squared are: 1, 4, 9, 36, 49, 196, 441, 1764. The sum of the squared divisors is 2500 which is 50 * 50, a square!

Given two integers m, n (1 <= m <= n) we want to find all integers between m and n whose sum of squared divisors is itself a square. 42 is such a number.

The result will be an array of arrays(in C an array of Pair), each subarray having two elements, first the number whose squared divisors is a square and then the sum of the squared divisors.

Examples:

list_squared(1, 250) --> [[1, 1], [42, 2500], [246, 84100]]
list_squared(42, 250) --> [[42, 2500], [246, 84100]]


MY CODE - copy from here down;

//this function will be run for each number in the specified range to determine if the number passess all specifications in the directions;

```Javscript
function tester(value)
{
  var num = value;
  //this function find the divisibles of passed value;
  function findDivisbles(num)
  {

    returnArray = [];
    for(var i = 1; i <= num/2; i++)
    {
      var check = num / i;
      if(check % 1 === 0)
      {
       returnArray.push(i);
      }
    }

    returnArray.push(num);

    //returns array of the divisible numbers;
    return returnArray;
  }

  var divisibles = findDivisbles(num);

//find the sum of the multiples;

  function createSquare(array)
  {
    for(var i = 0; i < array.length; i++)
    {
     array[i] = array[i] * array[i];
    }
    return array;
  }

  var squaredArray = createSquare(divisibles);
// console.log('the squaredArray: ', squaredArray);

  function findSum(array)
  {
    var sum = 0;
    for(var i = 0; i < array.length; i++)
    {
      sum += array[i];
    }
    return sum;
  }
  var sum = findSum(squaredArray);
// console.log('the sum: ', sum);

  //checks the sum of the divisible numbers
  var check = Math.sqrt(sum);
  if(check % 1)
  {
    return 'fail';
  }
  else
  {
    return sum;
  }
}

//runs the range between two points
function listSquared(m, n)
{
  var ansArray = [];


  for(var i = m; i <= n; i++)
  {
    var temp = [];
    //test if value passess the specifications
    if(tester(i) !== 'fail')
    {
      //if pass, pushes array of current value and the sum of the squared divisibles;
      temp.push(i);
      temp.push(tester(i));
      ansArray.push(temp);
    }
  }
  return ansArray;
}
```
