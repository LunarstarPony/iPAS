## DVWA

#### Platform install

##### 1, Install Docker by typing `sudo apt install -y docker.io`
##### 2, Install Docker Image by Typing `docker run --rm -it -p 80:80 vulnerables/web-dvwa`

![alt text](https://github.com/LunarstarPony/iPAS/blob/main/Class_Files/11_18_2020/1.png?raw=true)

##### 3, Access Network interface using port 80 

![alt text](https://github.com/LunarstarPony/iPAS/blob/main/Class_Files/11_18_2020/2.png?raw=true)

##### 4, setup Database by clicking Create/Reset Database

![alt text](https://github.com/LunarstarPony/iPAS/blob/main/Class_Files/11_18_2020/3.png?raw=true)

##### 5, Success! 

![alt text](https://github.com/LunarstarPony/iPAS/blob/main/Class_Files/11_18_2020/4.png?raw=true)

##### Source Code
```
<?php

if( isset( $_POST[ 'Submit' ]  ) ) {
    // Get input
    $target = $_REQUEST[ 'ip' ];

    // Determine OS and execute the ping command.
    if( stristr( php_uname( 's' ), 'Windows NT' ) ) {
        // Windows
        $cmd = shell_exec( 'ping  ' . $target );
    }
    else {
        // *nix
        $cmd = shell_exec( 'ping  -c 4 ' . $target );
    }

    // Feedback for the end user
    echo "<pre>{$cmd}</pre>";
}

?>
```