# MailDrop NodeJS API

APIs to get mails object from https://maildrop.cc

# install

with [npm](https://www.npmjs.com/package/@maildrop/api) do:

```
npm install --save @maildrop/api
```

# usage

for basic test

```js
const mails = await maildrop.getMails("linto@maildrop.cc");
console.log(`${mails.length || "zero"} mails`);

for (const mail of mails)
  console.log(`==========\n${JSON.stringify(mail, null, 2)}\n==========`);
```

### getMails(email)

fetch mails from corresponding email
@return Object[] sample { id, from, to, subject, date, body, html }[]

| opt   | type                | description                         |
| ----- | ------------------- | ----------------------------------- |
| email | <code>String</code> | [required] sample linto@maildrop.cc |

```json
{
  "id": "HrYSsdRcRA",
  "from": "Linto Cheeran <linto.cet@gmail.com>",
  "to": "linto",
  "subject": "subject",
  "date": "2020-04-08T21:47:13Z",
  "body": "raw email body",
  "html": "html body"
}
```

### deleteMail(email, id)

delete individual mail
@return [Object] `{ deleted: true }`

| opt   | type                | description                          |
| ----- | ------------------- | ------------------------------------ |
| email | <code>String</code> | [required] sample linto@maildrop.cc  |
| id    | <code>String</code> | [required] individual mail object id |

```js
for (const mail of mails)
  console.log(await maildrop.deleteMail("linto", mail.id));
```

### getApiKey()

return `x-api-key`, you can use this http header for advanced usage
