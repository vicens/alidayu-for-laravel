
[![Build Status](https://scrutinizer-ci.com/g/vicens/alidayu-for-laravel/badges/build.png?b=master)](https://scrutinizer-ci.com/g/vicens/alidayu-for-laravel/build-status/master)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/vicens/alidayu-for-laravel/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/vicens/alidayu-for-laravel/?branch=master)
[![Latest Stable Version](https://poser.pugx.org/vicens/alidayu-for-laravel/v/stable)](https://packagist.org/packages/vicens/alidayu-for-laravel)
[![Total Downloads](https://poser.pugx.org/vicens/alidayu-for-laravel/downloads)](https://packagist.org/packages/vicens/alidayu-for-laravel)
[![License](https://poser.pugx.org/vicens/alidayu-for-laravel/license)](https://packagist.org/packages/vicens/alidayu-for-laravel)


### 阿里云通信(阿里大于) For Laravel
阿里大于，是阿里通信旗下优质便捷的云通信服务平台，整合了三大运营商的通信能力，为开发者提供简洁易用的短信／语音API，三网合一通道，按需付费。阿里集团技术保障，实时、稳定、到达率高！

阿里云通信官网: [https://dayu.aliyun.com](https://dayu.aliyun.com)

阿里云通信API文档: [https://api.alidayu.com/doc2/apiList.htm](https://api.alidayu.com/doc2/apiList.htm)

阿里云通信SDK: [http://github.com/vicens/alidayu](http://github.com/vicens/alidayu)

### 环境要求
 - [illuminate\support](https://github.com/illuminate/support) ^5.1
 - [vicens\alidayu](http://github.com/vicens/alidayu) ^1.0
 
### 安装
 
 ```shell
composer require vicens/alidayu-for-laravel
```

### 使用

#### Laravel5.5以下需要注册服务提供者
在`config/app.php`的`provider`数组中, 添加`\Vicens\AlidayuForLaravel\Providers\AlidayuServiceProvider`:
```php
'providers' => [
    // Other service providers...
    \Vicens\AlidayuForLaravel\Providers\AlidayuServiceProvider::class
]
```

#### 设置配置
在`config/services.php`中,添加配置
```php
return [
    // other service config
    'alidayu' => [
        'appKey' => '23356838',
        'appSecret' => '254fee5fbabe2e01be04581d855c9af3',
        'sandbox' => false
    ]
];
```

#### 调用API

```php
use Vicens\Alidayu\Alidayu;
// 发送短信通知
$sms = Alidayu::sms($recNum, $smsTemplateCode, $smsFreeSignName, $smsParam, $extend);
// 发送请求并返回响应
$response = $sms->send();

if ($response->success()) {
    // 接口返回成功
    print_r($response->getData());
} else {
    // 接口返回错误
    echo $response->getError();
}

```


### 已支持的接口列表

 - [发送短信通知](https://github.com/vicens/alidayu/blob/master/src/Request/Sms.php)
 - [查询短信发送记录](https://github.com/vicens/alidayu/blob/master/src/Request/SmsQuery.php)
 - [语音通知](https://github.com/vicens/alidayu/blob/master/src/Request/SingleCall.php)
 - [文字转语音通知](https://github.com/vicens/alidayu/blob/master/src/Request/TtsSingleCall.php)
 - [多方语音通话](https://github.com/vicens/alidayu/blob/master/src/Request/DoubleCall.php)
 - [流量直充](https://github.com/vicens/alidayu/blob/master/src/Request/FlowCharge.php)
 - [流量直充分省](https://github.com/vicens/alidayu/blob/master/src/Request/FlowChargeProvince.php)
 - [流量直充查询](https://github.com/vicens/alidayu/blob/master/src/Request/FlowQuery.php)
 - [流量直充档位表](https://github.com/vicens/alidayu/blob/master/src/Request/FlowGrade.php)
 

