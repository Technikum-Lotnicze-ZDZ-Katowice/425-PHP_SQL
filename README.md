# 425-PHP_SQL



## CONNECTION

```php
    $con = mysqli_connect("localhost","root","","moja_baza");

    // Check connection
    if (mysqli_connect_errno()) {
        echo "Failed to connect to MySQL: " . mysqli_connect_error();
        exit();
    } else {
      echo "CONNECTION OK";
    }
```

##C.R.U.D operations

### CREATE

```php
       if(isset($_POST['add'])){
        if(!empty($_POST['imie']) && !empty($_POST['nazwisko']) && !empty($_POST['wiek'])){
            echo 'DODAWANIE ' . $_POST['imie'] . $_POST['nazwisko'] . $_POST['wiek'];
        
$addsql = "INSERT INTO users (id, imie, nazwisko, wiek) VALUES (NULL,'" . $_POST['imie'] ."','" . $_POST['nazwisko'] . "','" . $_POST['wiek'] ."')";
        
            if(mysqli_query($con,$addsql)){
                echo "RECORD ADDED";
            } else {
                echo "ADD ERROR";
            };
        } else {
            echo '<p style="color:red">Wypełnij wszystkie pola</p>';
        }
```

### READ

```php

        $sql = "SELECT * FROM users";

        $result = mysqli_query($con,$sql);
        
        echo '<table border="1">';
        while($row = mysqli_fetch_assoc($result)){

            echo "<tr>";
            echo "<td>" . $row['id'] . "</td>";
            echo "<td>" . $row['imie'] . "</td>";
            echo "<td>" . $row['nazwisko'] . "</td>";
            echo "<td>" . $row['wiek'] . "</td>";
            echo "</tr>";
        }
        echo "</table>";
```

### DELETE

```php
            $delsql = "DELETE FROM users WHERE id=10";
            
            if(mysqli_query($con,$delsql)){
                echo "RECORD DELETED";
            } else {
                echo "DELETE ERROR";
            };
```
