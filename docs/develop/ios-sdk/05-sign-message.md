---
sidebar_position: 5
---

# Sign Message

Use UniPass Wallet to sign the specified message, which can be done by calling `signMessage`. There are two message signature methods, `PersonalSign` and `SignTypedData`

## Type definitions:

```swift
public enum UniPassSignType: String {
    case PersonalSign
    case SignTypedData
}

public class UniPassSignInput: NSObject {
    public var from: String = ""
    public var type: UniPassSignType = .PersonalSign
    public var msg: String = ""
}

```

## Sample Code

```swift
// Ensure that the user is authorized to log in
if let userInfo = unipassSdk?.getUserInfo() {
    let signInput = UniPassSignInput()
    signInput.from = userInfo.address
    signInput.type = UniPassSignType.PersonalSign
    signInput.msg = signTextField?.text ?? "Test Sign Message"
        
    unipassSdk?.signMessage(signInput, SuccessBlock: { signature in
        print("unipassSdk: sign message successfully ✅", signature)
        self.signatureLabel?.text = signature
    }, ErrorBlock: { error in
        print("unipassSdk: sign message failed ❎", error)
    })
} else {
    print("unipassSdk: user not login ❎")
}

```
