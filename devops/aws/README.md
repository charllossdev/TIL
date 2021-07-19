# AWS

# EC2

## EC2 instance connect

```ruby
- ssh -i {full path of your .pem file} ec2-user@{instance IP address}

- ssh -i 'c:\Users\yourusername\.ssh\MyKeyPair.pem' ec2-user@{IP_Address}

- ssh -i '/Users/joongkeunlee/work/dev/config/aws/airi-key.pem' ec2-user@52.79.129.44
```

### AWS에서 제공하는 접속 가이드 에서 이러한 항목이 있다.

* SSH가 작동하려면 키가 공개적으로 표시되지 않아야 합니다.
  필요할 경우 이 명령을 사용합니다.
  ```ruby
  chmod 400 MyKeyPair.pem
  ```
