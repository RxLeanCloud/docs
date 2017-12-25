# <a name="sms-for-user"></a> 用户验证短信使用指南 {#sms-for-user} 

## <a name="sign-up-by-sms"></a> 使用手机号+验证码注册 _User {#sign-up-by-sms} 


<pre><code class="swift">
var user = RxAVUser()
user.mobilePhoneNumber = "13812345678"
user.email = "jun.wu@leancloud.rocks"
user.password = "leancloud"
user.set(key: "nickName", value: "WuJun")

user.sendSignUpSMS().flatMap { (sms) -> Observable&#60;Bool> in
    sms.setShortCode(receivedShortCode: "064241")
    return user.signUpWithSms(sms: sms)
}.subscribe(onNext: { (success) in
    if success {
        print("sign up successful")
    }
})
</code></pre>

<pre><code class="ts">
let user = new RxAVUser();
user.mobilephone = '13812345678';
user.email = 'jun.wu@leancloud.rocks'
user.password = 'leancloud';
user.set('nickName', 'WuJun');

user.sendSignUpSMS().flatMap(sms => {
    sms.shortCode = '064241';
    return user.signUpWithSms(sms);
}).subscribe(success => {
    console.log('sign up successful');
});
</code></pre>


