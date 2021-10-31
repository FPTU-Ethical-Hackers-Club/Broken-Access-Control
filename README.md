# Access control vulnerabilities and privilege escalation

- [Lý thuyết về Access Control](https://github.com/FPTU-Ethical-Hackers-Club/Broken-Access-Control/blob/main/Broken%20Access%20Control.md)
- [Lý thuyết về Insecure direct object references](https://github.com/FPTU-Ethical-Hackers-Club/Broken-Access-Control/blob/main/IDOR_PoC.md)
- [Các bài lab về Broken Access control theo chủ đề]:

  - [Unprotected functionality](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality)

  - [Unprotected functionality with unpredictable URL](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality-with-unpredictable-url)

  - [User role controlled by request parameter](https://portswigger.net/web-security/access-control/lab-user-role-controlled-by-request-parameter)

  - [User role controlled by hidden request parameter but leaked in response](https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile)

  - [Broken access control resulting from non-standard HTTP headers (X-Original-URL, X-Rewrite-URL)](https://portswigger.net/web-security/access-control/lab-url-based-access-control-can-be-circumvented)

  - [Broken access control by alternate HTTP request methods when performing an action](https://portswigger.net/web-security/access-control/lab-method-based-access-control-can-be-circumvented)

  - Horizontal privilege escalation: [User ID controlled by request parameter](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter), [User ID controlled by request parameter, with unpredictable user IDs](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids), [User ID controlled by request parameter with data leakage in redirect](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect).

  - Horizontal to vertical privilege escalation: [User ID controlled by request parameter with password disclosure](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure)

  - [Multi-step process with no access control on one step](https://portswigger.net/web-security/access-control/lab-multi-step-process-with-no-access-control-on-one-step)
  
  - [Referer-based access control](https://portswigger.net/web-security/access-control/lab-referer-based-access-control)

  - [Insecure direct object references](https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references)

- [Sử dụng extension Autorize và AutoRepeater của Burp Suite để tự động test các lỗi Broken Access Control](https://www.youtube.com/watch?v=3K1-a7dnA60&t=572s&ab_channel=ST%C3%96K)

- [Hướng dẫn cài Autorize và AutoRepeater]()
