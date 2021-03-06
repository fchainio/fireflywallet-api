# 萤火钱包轻应用接口api


## 示例

### 安装
``` 
npm install fireflywallet-api --save
```

### ready

``` javascript
import FireFlyWallet from 'fireflywallet-api';
const FFWProxy = new FireFlyWallet();
FFWProxy.ready().then(FFW=>{
  console.log('firefly wallet api is ready')
}).catch(err=>{
  console.error(err)
})
```

### 获取萤火钱包版本号
``` javascript
  FFWProxy.version
```
或者
``` javascript
  FFWProxy.getVersion().then(version=>{
    console.log(version)
  }).catch(err=>{
    console.error(err)
  })
```

### 获取当前运行平台
``` javascript
  FFWProxy.platform
```
或者
``` javascript
  FFWProxy.getPlatform().then(platform=>{
    console.log(platform);
  }).catch(err=>{
    console.error(err);
  })
```

### 获取当前账户恒星公钥
``` javascript
  FFWProxy.accountID
```
或者
``` javascript
  FFWProxy.getAccountID().then(accountID=>{
    console.log(accountID)
  }).catch(err=>{
    console.log(err)
  })
```

### 获取当前账户名称
```javascript
  FFWProxy.accountName
```
or
``` javascript
  FFWProxy.getAccountName().then(accountName=>{
    console.log(accountName)
  }).catch(err=>{
    console.log(err)
  })
```

### 获取当前设备UUID(原始数据做了sha256处理)
``` javascript
  FFWProxy.UUID
```
或者
``` javascript
  FFWProxy.getUUID().then(uuid=>{
    console.log(uuid);
  }).catch(err=>{
    console.error(err)
  })
```

### 获取当前萤火钱包的语言
``` javascript
  FFWProxy.locale
```
或者
``` javascript
  FFWProxy.getLocale().then(locale=>{
    console.log(locale)
  }).catch(err=>{
    console.error(err)
  })
```

### 获取用户当前的horizon地址
``` javascript
  FFWProxy.horizonUrl
```
or
``` javascript
  FFWProxy.getHorizonUrl().then(horizonUrl=>{
    console.log(horizonUrl)
  }).catch(err=>{
    console.error(err)
  })
```

### 获取当前horizon网络的密语
``` javascript
  FFWProxy.network
```
or
``` javascript
  FFWProxy.getNetwork().then(network=>{
    console.log(network)
    //输出: "Public Global Stellar Network ; September 2015" or "Test SDF Network ; September 2015"
  }).catch(err=>{
    console.error(err)
  })
```


### 获取当前账户余额
``` javascript
FFWProxy.getBalances().then(balances=>{
  console.log(balances)
}).catch(err=>{
  console.error(err)
})
```

### 数据签名，待签名的数据必须为JSON格式
``` javascript
let data = { accountid: 'GG', time: new Date().getTime() }
FFWProxy.sign(data).then(result=>{
  console.log(result)
}).catch(err=>{
  console.error(err)
})
```

### 支付
``` javascript
FFWProxy.pay({
  destination: 'GCKKUWHT3ILQWWKQ3MUOCAC7LRJNLCOES7SEI6TCQVGZD4GCULO2PGNU', 
  code: 'XFF', 
  issuer: 'GAZEX2USUBMMWFRZFS77VDJYXUFLXI4ZGFPWX6TBNZCSTEQWNLFZMXFF', 
  amount: 1, 
  memo_type: 'TEXT', //取值见stellar的api文档
  memo: 'Hello,FFW'
}).then(data=>{
  console.log('pay success');
}).catch(err=>{
  console.error(err)
})
```

### 路径支付
``` javascript
FFWProxy.pathPayment({
  destination: 'GCKKUWHT3ILQWWKQ3MUOCAC7LRJNLCOES7SEI6TCQVGZD4GCULO2PGNU', 
  code: 'XFF', 
  issuer: 'GAZEX2USUBMMWFRZFS77VDJYXUFLXI4ZGFPWX6TBNZCSTEQWNLFZMXFF', 
  amount: 1, 
  memo_type: 'TEXT', 
  memo: 'Hello,FFW'
}).then(data=>{
    console.log('pathpayment success')
  }).catch(err=>{
    console.error(err)
  })
```

### 授信
``` javascript
let code = 'XFF';
let issuer = 'GAZEX2USUBMMWFRZFS77VDJYXUFLXI4ZGFPWX6TBNZCSTEQWNLFZMXFF';
FFWProxy.trust(code,issuer).then(data=>{
    console.log('trust success')
  }).catch(err=>{
    console.error(err)
  })
```

### XDR签名（签名后的XDR可以提交到horizon）
``` javascript
let xdr = 'AAAAAEpng8wi7nIqz02/1bmC4I5jzz763WoadKIWy7M5MVc3AAAAZACHjkkAAAABAAAAAAAAAAAAAAABAAAAAAAAAAoAAAALaG9tZV9kb21haW4AAAAAAQAAABBodHRwOi8vZmNoYWluLmlvAAAAAAAAAAA='
FFWProxy.signXDR(xdr,"签名XDR").then(data=>{
    console.log(`签名后的XDR:${data}`)
  }).catch(err=>{
    console.error(err)
  })
```

### 扫描
``` javascript
FFWProxy.scan().then(data=>{
  console.log(`扫描结果：${data}`);
}).catch(err=>{
  console.error(err)
})
```

### 分享
``` javascript
let options = {
  message: '分享图片',
  files: ['base64格式的图片']
}
FFWProxy.share(options).then(data=>{
  console.log('share success')
}).catch(err=>{
  console.error(err)
})
```

### 返回原始FFW对象
``` javascript
FFWProxy.origin
//output: window.FFW

或者

FFWProxy.getOrigin().then(FFW => {
  console.log(FFW)
}).catch(err => {
  console.error(err)
})
```

### 如果想直接在浏览器中使用
``` javascript
  <script src="path\to\dist\fireflywallet.min.js"></script>
  <script>
    var FFWProxy = new FireFlyWallet();
    FFWProxy.ready().then(function(FFW){
      console.log('firefly wallet is ready!')
    }).catch(function(err){
      console.error(err);
    })
  </script>
```