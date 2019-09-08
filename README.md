# differencebetweentwotimestringsinphp
A program to calculate the difference between two time strings and return a result in string - written in PHP

It simply takes in two time strings with this format '00:00:00' and calculates the difference between them, then returns a formatted string to look the same as the ones provided.

It takes care of negative results and returns the exact time difference in hours, minutes and seconds.

Just pass the two times as parameter to the function, with the second parameter expected to be the most recent time, as shown below;

    $time1 = "21:00:00";
    $time2 = "07:00:00";
    echo dateDifference($time1, $time2);
    
 Note, this function can and should be broken down into smaller discrete functions, but for some reason, I simply put everything into the dateDifference function for a straightput shot. 
