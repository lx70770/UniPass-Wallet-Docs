---
sidebar_position: 6
---

# Logout Account

## Sample Code

```java
// logout will clear local upAccount data
unipassInstance.logout(object : UnipassCallBack<Void> {
    override fun success(output: Void?) {
        Log.d("Unipass Logout", "success")
    }
    override fun failure(error: Exception) {
        Log.d("Unipass Logout", error.message ?: "Something went wrong")
    }
})
```
