# unimal-py-sdk

This is a Python SDK for Unimail. Quickly integrate into your project

[中文文档](README_zh.md)

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [unimal-py-sdk](#unimal-py-sdk)
  - [simple usage](#simple-usage)
  - [api docs](#api-docs)
  - [support language](#support-language)

<!-- /code_chunk_output -->

## simple usage

- init a unimail client

you need a authorization key.

main.py

```python
from unimail-py-sdk import Client, Result

# please input your key here
key: str = ""

client: Client = Client(key)

client.check_connect()
```

- send email

example
receiver: aaa@gmail.com  
email subject: email subject  
email content: this is a email content

```python
    result: Result := client.send_email("aaa@gmail.com", "email subject", "this is a email content")

    if result.is_success:
        print("send email success")
    else:
        print(f"send email fail, error: {result.msg}")
```

- batch send email

example
receivers: aaa@gmail.com,bbb@gmail.com  
email subject: email subject  
email content: this is a email content

```python
    result: Result := client.batch_send_email("aaa@gmail.com", "email subject", "this is a email content")

    if result.is_success:
        print("send email success")
    else:
        print(f"send email fail, error: {result.msg}")
```

## api docs

1. Client(key: str, host: str, data: str, obj: json): Client

init a client by key

4. client.set_language(language :str) -> bool

set language for the client,default is zh

5. client.check_connect() -> bool

check the host and key is ok

6. client.send_email(receiver :str, subject :str, content :str) -> Result

send email to receiver. if you have many receiver, you can concat the receiver by ";" or use BatchSendEmail

7. client.batch_send_email(receivers :list, subject :str, content :str) -> Result

like SendEmail, but receivers is a slice

## support language

chinese is the default language for the sdk.

- [x] english (en)
- [x] simple chinese (zh)
- [x] vietnamese (vi)
- [x] idonesian (id)
- [x] thai (th)
- [x] gujarati (gu)

if you want to support other language, please open a issue.
