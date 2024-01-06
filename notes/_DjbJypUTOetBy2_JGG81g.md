<?php
$Link=mysql_connect('localhost','root','00001111') or die(mysql_error());
mysql_select_db(test,$Link) or die(mysql_error());
mysql_query("SET NAMES 'UTF8'",$Link);
if(!empty($Link))
{
	echo 'success';
}
else
{
	echo 'failed';	
}
//$sql="select * from student Order by 'student_id'";
//$sql="select * from student Order by student_id DESC";
//$sql="select * from student WHERE student_address LIKE '台中市'";
$sql="select * from student WHERE student_points > 50 order by student_points DESC";
//echo $sql;
$result=mysql_query($sql);
$num=mysql_num_rows($result);
//echo $num;
/*while($row=mysql_fetch_array($result))
{
	echo $row["student_name"].'<br>';
}*/
$_html=array();
while($row=mysql_fetch_array($result))
{
	$_html[]=$row;

}?>
<table border='1' cellspacing='1' cellpadding='6'>
	  	<tr>
			<td>編號</td>
			<td>姓名</td>
			<td>地址</td>
            <td>點數</td>
		</tr>
<?php foreach($_html as $key => $val){ ?>
<tr><td>
<?php echo $val['student_id'] ?>
</td><td>
<?php echo $val['student_name'] ?>
</td><td>
<?php echo $val['student_address'] ?>
</td><td>
<?php echo $val['student_points'] ?>
</td></tr>
<?php } ?>
</table>
