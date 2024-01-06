https://223.27.34.183:8443/
帳號：bmidp888
密碼：B&7G6kmq&%CaBBhB


<?php
//$Link = mysql_connect('localhost', 'root', '00001111') or die(mysql_error());
//mysql_select_db('test', $Link) or die(mysql_error());
//mysql_query("SET NAMES 'UTF8'", $Link);
session_start();
require_once('connect.php');

$acc = $_POST['acc'];
$password = $_POST['password'];
//echo $acc.','.$password;

if(empty($acc) || empty($password)){

	//exit('錯誤');
	//如果其中一項資料為空，導回index.php
	header('Location: index.php');
}

$sql = "select * from admin WHERE admin_acc = '".mysql_real_escape_string($acc)."' AND admin_password = '".mysql_real_escape_string($password)."'";
$result = mysql_query($sql);
$admin_data = mysql_fetch_array($result);

if(!empty($admin_data))
{
	//echo '登入成功';
	$sql = "UPDATE admin SET admin_logintime = now() WHERE admin_id = '".$admin_data['admin_id']."'";
	mysql_query($sql);
	$_SESSION['admin_id'] = $admin_data['admin_id'];
	$_SESSION['admin_acc'] = $admin_data['admin_acc'];
	$_SESSION['admin_name'] = $admin_data['admin_name'];

	header('Location: control.php');
}
else
{	
	//如果帳號密碼錯誤，利用javascript導回index.php
	//echo '登入失敗';
	//清除資料
	session_unset();
?>
	<script type = "text/javascript">
		alert('帳號密碼錯誤,請重新輸入');
		window.location.href = 'index.php';
	</script>
<?php
}
?>

<!---->
<body>
		<center>
			<div style = "margin-top: 50px;">
				<form action = "login.php" method = "post">
					<table border = "1" cellpadding = "10">
						<tr>
							<td>使用者帳號</td>
							<td><input type = "text" name = "acc" value = ""></td>
						</tr>
						<tr>
							<td>使用者密碼</td>
							<td><input type = "password" name = "password" value = ""></td>
						</tr>
						<tr>
							<td colspan = "2" align = "center"><input type = "submit" value = "登入"></td>
						</tr>
					</table>
				</form>
			</div>
		</center>
	</body>