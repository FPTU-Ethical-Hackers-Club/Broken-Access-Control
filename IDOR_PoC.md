# KBID 268 - Insecure direct object references

#### Created by [Glenn ten Cate](https://github.com/blabla1337/skf-labs)

## Running the app

```
$ sudo docker pull blabla1337/owasp-skf-lab:idor
```

```text
$ sudo docker run -ti -p 127.0.0.1:5000:5000 blabla1337/owasp-skf-lab:idor
```

{% hint style="success" %}
Now that the app is running let's go hacking!
{% endhint %}

## Running the app Python3

First, make sure python3 and pip are installed on your host machine.
After installation, we go to the folder of the lab we want to practise 
"i.e /skf-labs/XSS/, /skf-labs/jwt-secret/ " and run the following commands:

```
$ pip3 install -r requirements.txt
```

```
$ python3 <labname>
```

{% hint style="success" %}
 Now that the app is running let's go hacking!
{% endhint %}


![image](https://user-images.githubusercontent.com/61876488/139566394-a7266859-d2d0-44d1-a5ab-9aef7fdb3a96.png)

## Reconnaissance

Insecure Direct Object References occur when an application provides direct access to objects based on user-supplied input. As a result of this vulnerability attackers can bypass authorization and access resources in the system directly, for example database records or files.

Insecure Direct Object References allow attackers to bypass authorization and access resources directly by modifying the value of a parameter used to directly point to an object. Such resources can be database entries belonging to other users, files in the system, and more. This is caused by the fact that the application takes user supplied input and uses it to retrieve an object without performing sufficient authorization checks.

Lets look at an example:

```text
http://foo.bar/somepage?invoice=12345
```

In this case, the value of the invoice parameter is used as an index in an invoices table in the database. The application takes the value of this parameter and uses it in a query to the database. The application then returns the invoice information to the user.

Since the value of invoice goes directly into the query, by modifying the value of the parameter it is possible to retrieve any invoice object, regardless of the user to whom the invoice belongs.

## Exploitation

Step 1:

The application allows the user to create a PDF file and retrieve the file with the index assigned to it:

![image](https://user-images.githubusercontent.com/61876488/139566407-5a4fe2a3-4603-40b4-8e88-486cac2bb76c.png)

HTTP Request for Document Creation:

![image](https://user-images.githubusercontent.com/61876488/139566412-7835f56b-62b5-422e-84ec-aa1a771f68bb.png)

![image](https://user-images.githubusercontent.com/61876488/139566416-1d66bc01-8995-4437-b15d-85a8ab823a2e.png)

Step 2:

Let's try to brute force if we can access other documents by fuzzing the index, consider the index ID=2000 for example:

![image](https://user-images.githubusercontent.com/61876488/139566479-c27443a7-b8e8-4269-883e-fcaa988a5aec.png)

Ok, that's a good start so now we atleast know the index value falls between 1-1500.

Step 3: To further exploit and attempt to access other indexed documents, we would use a tool called burpsuite which would help us automate the fuzzing task.

```text
Please refer to the following link to configure burp suite for automating fuzzing task: 
https://www.hackingarticles.in/beginners-guide-burpsuite-payloads-part-1/
```

![image](https://user-images.githubusercontent.com/61876488/139566485-26b21458-4b3c-4563-9bce-e91ae037b33f.png)

So from the fuzzing results, if we observe closesly the index ID="51" seems interesting as the other ID's seem to have the same response length. Let's check what do we achieve with ID=51.

![image](https://user-images.githubusercontent.com/61876488/139566489-dca5828b-3a79-434b-bbb5-c0d531c51f89.png)

![image](https://user-images.githubusercontent.com/61876488/139566493-6fe815bf-497d-47df-a362-7c8b55d5b0f0.png)

![image](https://user-images.githubusercontent.com/61876488/139566497-1ff2ff51-6e72-4ceb-a99d-8dae7768eff6.png)

And we captured the right flag :-\), so we could access the document belonging to some other user bypassing access controls of the application.

## Additional Sources

Please refer to the link below for more details around IDOR:

{% embed url="https://www.owasp.org/index.php/Top\_10\_2013-A4-Insecure\_Direct\_Object\_References" caption="" %}

