<?php
    $DEBUG = false;
    error_reporting(0);

    if ($DEBUG)
    {
        error_reporting(E_ALL);
        ini_set('display_errors', 'On');
    }

    register_shutdown_function("functionNotFound");
    function functionNotFound()
    {
        $last_error = error_get_last();
        if ($last_error['type'] === E_ERROR)
            echo "Function not found!";
    }

    // utils
    $blacklist = array("system", "passthru", "exec", "read", "open", "eval", "backtick", "flag", "`", "_");
    function contains($s,$a)
    {
        foreach ($a as $value)
        {
            if (stristr($s,$value))
            {
                return 1;
            }
        }
        return 0;
    }

    // user define functions
    function hello($name)
    {
        echo "Hello $name! I put something interesting in flag.php.</br></br>";
    }

    function source()
    {
        highlight_file(__FILE__);
        exit();
    }


    if(count($_GET) > 0)
    {
        if(contains($_SERVER['REQUEST_URI'],$blacklist))
        {
            echo $_SERVER['REQUEST_URI'];
            die("Hacker detected!!");
        }
        #echo `ls`;
        list($key, $val) = each($_GET);

        if (strlen($key) > 6)
        {
            die("Function name is too long! Hacker detected!!");
        }

        $key($val);
    }
?>

<form>
What's your name? I have something to tell you. <br/>
<input type="text" name="hello">
<button type="submit" value="Submit">Submit</button>
</form>

<!--
function hello($name) { ... }
function source() { ... }
-->