#Jenkinsfile
- Declaritive: SCM checkout automatically, can restart from specific stage 
- Scripted: cannot do the above

# Env
```
environment {
  SERVER_CREDS=credentials('server-creds')   #username+password
}
echo "username=${SERVER_CREDS}"     #username:password in ecrypted format
echo "username=${SERVER_CREDS_USR}"
echo "username=${SERVER_CREDS_PSW}"
```

![image](https://github.com/user-attachments/assets/394e4f6c-f509-447a-acaf-c3e09ebef983)
![image](https://github.com/user-attachments/assets/9e2c5377-5c04-4cd9-8a33-fc753a790a60)


