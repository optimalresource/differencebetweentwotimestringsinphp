# differencebetweentwotimestringsinphp
A program to calculate the difference between two time strings and return a result in string - written in PHP

It simply takes in two time strings with this format '00:00:00' and calculates the difference between them, then returns a formatted string to look the same as the ones provided.

It takes care of negative results and returns the exact time difference in hours, minutes and seconds.

Just pass the two times as parameter to the function, with the second parameter expected to be the most recent time, as shown below;

    $time1 = "21:00:00";
    $time2 = "07:00:00";
    echo dateDifference($time1, $time2);
    
Note, this function can and should be broken down into smaller discrete functions, but for some reason, I simply put everything into the dateDifference function for a straightput shot. 
 
Here is the php function below;

    function dateDifference($time1, $time2) {
        $firstHour = $time1[0] . $time1[1];
        $firstMin = $time1[3] . $time1[4];
        $firstSec = $time1[6] . $time1[7];

        $h_to_sec = $firstHour * 60 * 60;
        $m_to_sec = $firstMin * 60;
        $total_sec1 = $h_to_sec + $m_to_sec + $firstSec;

        $secondHour = $time2[0] . $time2[1];
        $secondMin = $time2[3] . $time2[4];
        $secondSec = $time2[6] . $time2[7];

        $h_to_sec = $secondHour * 60 * 60;
        $m_to_sec = $secondMin * 60;
        $total_sec2 = $h_to_sec + $m_to_sec + $secondSec;

        if($total_sec1 < $total_sec2) {
            $time_difference = $total_sec2 - $total_sec1;   
        }else {
            $time_difference = $total_sec1 - $total_sec2;
        }

        $sec_to_h_fraction = $time_difference / 3600;
        $sec_to_h = floor($sec_to_h_fraction);
        $min_remainder = $sec_to_h_fraction - $sec_to_h;

        $sec_to_m_fraction = $min_remainder * 60;
        $sec_to_m = floor($sec_to_m_fraction);
        $sec_remainder = $sec_to_m_fraction - $sec_to_m;

        $sec_to_s_fraction = $sec_remainder * 60;
        $sec_to_s = floor($sec_to_s_fraction);

        if($sec_to_h < 10) {
            $sec_to_h = '0' . $sec_to_h;
        }

        if($sec_to_m < 10) {
            $sec_to_m = '0' . $sec_to_m;
        }

        if($sec_to_s < 10) {
            $sec_to_s = '0' . $sec_to_s;
        }

        if($time1 < $time2) {
            $resultant = $sec_to_h . ':' . $sec_to_m . ':' . $sec_to_s;
        }else {
            $resultant = '-' . $sec_to_h . ':' . $sec_to_m . ':' . $sec_to_s;
        }
        return $resultant;
    }
