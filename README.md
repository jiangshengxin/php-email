# php-email
PHPEmail邮箱类

###安装
```apple js
composer require "jiangshengxin/email"
```

###使用查看 demo.php
```php
$mail = new \PHPMailer\PHPMailer();
        /*服务器相关信息*/
        $mail->IsSMTP();                 //设置使用SMTP服务器发送
        $mail->SMTPAuth = true;               //开启SMTP认证
        $mail->Host = 'smtp.163.com';        //设置 SMTP 服务器,自己注册邮箱服务器地址
        $mail->Username = 'jiangshengxin@163.com';  //发信人的邮箱名称
        $mail->Password = 'xxxxxxx';    //发信人的邮箱密码
        /*内容信息*/
        $mail->IsHTML(true);              //指定邮件格式为：html 不加true默认为以text的方式进行解析
        $mail->CharSet = "UTF-8";                 //编码
        $mail->From = 'jiangshengxin@163.com';             //发件人完整的邮箱名称
        $mail->SMTPSecure = 'tls';       //加密方式 "" or "ssl" or "tls"
        $mail->FromName = $user;             //发信人署名
        $mail->Subject = $title;             //信的标题
        $mail->MsgHTML($content);                 //发信主体内容

        if (!empty($fileUrl) && file_exists($fileUrl)) {  //附件
            $mail->AddAttachment($fileUrl);
        }

        //发送邮件 收件人地址
        if (is_array($addRess)) {  //群发 or 单发
            foreach ($addRess as $valRess) {
                $mail->AddAddress($valRess);
            }
        } else {
            $mail->AddAddress($addRess);
        }

        //使用send函数进行发送
        if ($mail->Send()) {
            return true;
        } else {
            //self::$error=$mail->ErrorInfo;
            return $mail->ErrorInfo;
        }
```


**搞定**