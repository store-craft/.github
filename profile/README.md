<div style="text-align:center">
  <div width="90%">
    <img src='https://github.com/store-craft/storecraft/blob/main/packages/docs/public/storecraft-color.svg' 
        width='100%' />
  </div>
  Ai First Javascript Commerce as Code backend
</div><hr/><br/>

# The <img src='https://github.com/store-craft/storecraft/blob/main/packages/docs/public/storecraft-color.svg' height='24px' style="transform: translateY(4px);" /> mono-repo

Hi 👋, `Storecraft` is a next generation Commerce As Code javascript backend.

⭐ run on any javascript [platform](https://storecraft.app/docs/backend/platforms/node) (deno, bun, node, workers, aws-lambda, google-functions), serverless / serverful

⭐ connect to any [database](https://storecraft.app/docs/backend/databases/sqlite) (mongo, sqlite, postgres, mysql, neon, turso, d1, planetscale)

⭐ use [storage](https://storecraft.app/docs/backend/storage/s3) (local, r2, s3 compatible, google and more)

⭐ It is [extensible and modular](https://storecraft.app/docs/backend/extensions/overview)

⭐ It is [event based](https://storecraft.app/docs/backend/events)

⭐ Boasts an official [Dashboard](https://storecraft.app/docs/dashboard/overview)

⭐ Well documented [REST-API](https://storecraft.app/docs/rest-api/api) (can also be found in your `/api/reference` endpoint)

<hr/>

  

## **GET STARTED WITH CLI NOW** 👇

```bash
npx storecraft create
```

Storecraft emphesizes modular commerce as code to achieve business logic,

```js
const app = new App({
  auth_admins_emails: ['tomer.shalev@gmail.com'],
  general_store_name: 'Wush Wush Games',
  // ... MORE Mandatory CONFIG
})
.withPlatform(new NodePlatform())
.withDatabase(new LibSQL())
.withStorage(new NodeLocalStorage('storage'))
.withMailer(new Resend())
.withPaymentGateways({
  paypal: new Paypal({ env: 'test' }),
  stripe: new Stripe(),
  dummy_payments: new DummyPayments(),
})
.withExtensions({
  postman: new PostmanExtension(),
})
.withAI(
  new OpenAI({ model: 'gpt-4o-mini'})
)
.withVectorStore(
  new LibSQLVectorStore({
    embedder: new OpenAIEmbedder(),
  })
)
.withAuthProviders({
  google: new GoogleAuth(),
})
.on(
  'order/checkout/complete',
  async (event) => {
    // send a team slack message
  }
).init();

await migrateToLatest(app._.db, false);
await app._.vector_store?.createVectorIndex();

http
.createServer(app.handler)
.listen(
  8000,
  () => {
    app.print_banner('http://localhost:8000');
  }
); 

```

**Will produce** a server

<div style='text-align: center' align="center">
  <img src='https://storecraft.app/storecraft-terminal-2.png' 
      width='70%' />
</div><hr/><br/>
```text
Author: Tomer Shalev (tomer.shalev@gmail.com)
```
