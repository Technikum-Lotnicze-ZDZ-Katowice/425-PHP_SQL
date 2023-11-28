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

### INSERT (CREATE RECORD)

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

//mysqli_fetch_row
//mysqli_fetch_array
//mysqli_fetch_assoc

            echo "<tr>";
            echo "<td>" . $row['id'] . "</td>";
            echo "<td>" . $row['imie'] . "</td>";
            echo "<td>" . $row['nazwisko'] . "</td>";
            echo "<td>" . $row['wiek'] . "</td>";
            echo "</tr>";
        }
        echo "</table>";
```
### UPDATE
```php
$updsql = "UPDATE users SET imie = '". $_POST['imie']."', nazwisko = '". $_POST['nazwisko']."', wiek = '". $_POST['wiek']."' WHERE id = " .$_POST['id'];

        if(mysqli_query($con,$updsql)){
             echo "RECORD UPDATED";
        } else {
             echo "ADD ERROR";
        };
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

ZADANIE 42601

Przygotuj zmodyfikowaną wersję kreatora zestawu komputerowego (prosty sklep internetowy opisany w zad z lekcji [422-PHP-forms](https://github.com/Technikum-Lotnicze-ZDZ-Katowice/422-PHP-forms) rozudowany o obsugę bazy danych:

1. Stwórz podstronę dodawanie zawierającą formularz dodawania produktu
2. Zapisz obrazy produktów w bazie danych (url)
3. Stwórz podstrony/podstronę z kategoriami produktów
4. Obsłuż akcję dodaj do koszyka (koszyk wyświetla się stale w prawym górnym rogu)
5. Zapisz koszyk w bazie danych

NA WYŻSZĄ OCENĘ:
- uploaduj obrazy na serwer (upload)
- uwzględnij kategorie produktów
- zaimplementu sortowanie
- zaimplementuj wyszukiwanie
- zadbaj o wygląd strony


NA OCENĘ CELUJĄCĄ - wszystkie powyższe punkty plus system logowania

https://miroslawzelent.pl/kurs-php/logowanie-do-strony-sesja-wstrzykiwanie-sql/


ZADANIE DODATKOWE - GRA RPG:
https://github.com/Technikum-Lotnicze-ZDZ-Katowice/SILPITS-GRA-RPG
