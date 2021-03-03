<?php

$name=$email=$website=$comment=$gender="";
$errname=$erremail=$errwebsite=$errgender="";

if($_SERVER["REQUEST_METHOD"]=="POST"){
    if(empty($_POST['name'])){
        $errname="<span style='color:red'>Name is required</span>";
    }else{
        $name= Vaidation($_POST["name"]);
    }

    if(empty($_POST['email'])){
        $erremail="<span style='color:red'>Email is required</span>";
    }else{
        $email= Vaidation($_POST["email"]);
    }
    if(empty($_POST['website'])){
        $erremail="<span style='color:red'>website is required</span>";
    }else{
        $errwebsite= Vaidation($_POST["website"]);
    }
      
    if(empty($_POST['gender'])){
        $erremail="<span style='color:red'>gender is required</span>";
    }else{
        $email= Vaidation($_POST["gender"]);
    }
    $comment= Vaidation($_POST["comment"]);
    
    

    echo "Name:".$name;
    echo "<br/>";
    echo "email:".$email;
    echo "<br/>";
    echo "website:".$website;
    echo "<br/>";
    echo "comment:".$comment;
    echo "<br/>";
    echo "gender:".$gender;
    

}



function Vaidation($data) {
$data= trim($data);
$data= stripcslashes($data);
$data= htmlspecialchars($data);
return $data;


}


?>





<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
<form method="post" action="<?php echo ($_SERVER['PHP_SELF']);?>">

<table>
<p style='color:red'>*Required field</p>
<tr>
<td>Name</td>
<td><input type="text" name="name"/>*<?php echo $errname;?></td>
</tr>
<tr>
<td>Email</td>
<td><input type="email" name="email"/>*<?php echo $erremail;?></td>
</tr>
<tr>
<td>Website</td>
<td><input type="text" name="website"/>*<?php echo $errwebsite;?></td>
</tr>
<tr>
<td>Comment</td>
<td><textarea name="comment" id="" cols="30" rows="4"></textarea></td>
</tr>
<tr>
<td>Gender</td>
<td>
<input type="radio" name="gender" value="Female"/>Female
<input type="radio" name="gender" value="male"/>male
*<?php echo $errgender;?>
</td>
</tr>
<tr>
<td></td>
<td><input type="submit" name="submit" value="submit"></td>
</tr>
</table>
</form>
</body>
</html>
