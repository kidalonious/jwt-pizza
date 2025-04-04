# Learning notes

## JWT Pizza code study and debugging

As part of `Deliverable ⓵ Development deployment: JWT Pizza`, start up the application and debug through the code until you understand how it works. During the learning process fill out the following required pieces of information in order to demonstrate that you have successfully completed the deliverable.

| User activity                                       | Frontend component | Backend endpoints | Database SQL |
| --------------------------------------------------- | ------------------ | ----------------- | ------------ |
| View home page                                      | home.tsx           | none              | none         |
| Register new user<br/>(t@jwt.com, pw: test)         | register.tsx       | [POST] '/api/auth'| INSERT INTO user (name, email, password) VALUES (?, ?, ?)<br/>INSERT INTO userRole (userId, role, objectId) VALUES (?, ?, ?)|
| Login new user<br/>(t@jwt.com, pw: test)            | login.tsx          | [PUT] '/api/auth' | INSERT INTO auth (token, userId) VALUES (?, ?) |
| Order pizza                                         | menu.tsx           |                   | INSERT INTO dinerOrder (dinerId, franchiseId, storeId, date) VALUES (?, ?, ?, now())<br/>INSERT INTO orderItem (orderId, menuId, description, price) VALUES (?, ?, ?, ?)             |
| Verify pizza                                        | delivery.tsx       | none              | none         |
| View profile page                                   | dinerDashboard.tsx | none              | none         |
| View franchise<br/>(as diner)                       | franchiseDashboard.tsx | none          | none         |
| Logout                                              | logout.tsx         | [DELETE] '/api/auth'| DELETE FROM auth WHERE token=?|
| View About page                                     | about.tsx          | none              | none         |
| View History page                                   | history.tsx        | none              | none         |
| Login as franchisee<br/>(f@jwt.com, pw: franchisee) | login.tsx          | [PUT] '/api/auth' | INSERT INTO auth (token, userId) VALUES (?, ?)|
| View franchise<br/>(as franchisee)                  | franchise.tsx      | none              | none         |
| Create a store                                      | createStore.tsx    | [POST] '/api/auth'| INSERT INTO store (franchiseId, name) VALUES (?, ?)             |
| Close a store                                       | closeStore.tsx     | [DELETE] '/api/auth'| DELETE FROM store WHERE franchiseId=? AND id=?             |
| Login as admin<br/>(a@jwt.com, pw: admin)           | adminDashboard.tsx | [PUT] '/api/auth' | INSERT INTO auth (token, userId) VALUES (?, ?)             |
| View Admin page                                     | adminDashboard.tsx | none              | none         |
| Create a franchise for t@jwt.com                    | createFranchise.tsx| [POST] '/api/auth'| SELECT id, name FROM user WHERE email=?<br/>INSERT INTO franchise (name) VALUES (?)<br/> INSERT INTO userRole (userId, role, objectId) VALUES (?, ?, ?)  |
| Close the franchise for t@jwt.com                   | closeFranchise.tsx | [DELETE] '/api/auth'| DELETE FROM store WHERE franchiseId=?<br/> DELETE FROM userRole WHERE objectId=?<br/>DELETE FROM franchise WHERE id=?            |
