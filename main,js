var func = prompt( 'Enter your f(x): ', '1 + 2 - 34 * 5 :(/) 6 ^ 2' );
var textArray = [];

for ( var i of func ) {
    if ( i != ' ' ) {
        textArray.push(i);
    }
}

var nums = '';
var resArray = [];
var error = 1;

for ( var i of textArray ) {
    if ( isFinite(i) ){
        nums += i;
        error = 0;
    } else {
        
          if ( !error ) {
            resArray.push(nums);
          }
        resArray.push(i);
        nums = '';
        error = 1;
    }
}
if (error == 0) {
    resArray.push(nums);
}

var res = [];
res = topPriority(resArray);
res = power(resArray);
res = firstCalc(resArray);
res = secondCalc(resArray); 

alert( 'the result is: ' + res );

function topPriority(rArray) {

    for ( var i = 0; i < rArray.length; i++) {
        if ( String(rArray[i]) == '(' ) {
            var n = i + 1;
            var count = 0;
            var countArray = [];
            var countRes = [];

            while ( String(rArray[n]) != ')' ) {
                count += 1;
                countArray.push( rArray[n] );
                n++;
            }


            countRes = power(countArray);
            countRes = firstCalc(countArray);
            countRes = secondCalc(countArray);
            
            var hooksRes = countRes[0];
            n = i + 1;
            rArray.splice( n , count + 1 );
            rArray.splice( (n - 1) , 1, hooksRes );

            i = 0;
        }
    }
    return rArray;
}

function power(rArray) {
    for ( var i = 0; i < rArray.length; i++) {
        if ( String(rArray[i]) == '^' ) {
            var result = rArray[i - 1] ** rArray[i + 1];
            rArray.splice( (i - 1) , 1);
            rArray.splice((i - 1) , 1, result);
            rArray.splice(i, 1);
            i = 0;
        }
    }
    return rArray;
}

function firstCalc(rArray) {
    for ( var i = 0; i < rArray.length; i++) {
        if ( ( String(rArray[i]) == '*' ) || ( String(rArray[i]) == ':' )
        || ( String(rArray[i]) == '/' ) ) {

            if (String(rArray[i]) == '*' ) {
                var result = rArray[i - 1] * rArray[i + 1];
            } else {
                var result = rArray[i - 1] / rArray[i + 1];
            }

            rArray.splice( (i - 1) , 1);
            rArray.splice((i - 1) , 1, result);
            rArray.splice(i, 1);
            i = 0;
        }
    }
    return rArray;
}

function secondCalc(rArray) {
    for ( var i = 0; i < rArray.length; i++) {
        if ( String(rArray[i]) == '+' || String(rArray[i]) == '-' ) {

            if (String(rArray[i]) == '+' ) {
                var result = +rArray[i - 1] + +rArray[i + 1];
            } else {
                var result = rArray[i - 1] - rArray[i + 1];
            }

            rArray.splice( (i - 1) , 1);
            rArray.splice((i - 1) , 1, result);
            rArray.splice(i, 1);
            i = 0;
        }
    }
    return rArray;
}
