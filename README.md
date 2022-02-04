This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Ceramic Problem

Upon running `yarn dev`, the following error appears in the terminal:

```
SyntaxError: Named export 'EthereumAuthProvider' not found. The requested module '@3id/connect' is a CommonJS module, which may not support all module.exports as named exports.
CommonJS modules can always be imported via the default export, for example using:

import pkg from '@3id/connect';
const {ThreeIdConnect: l}from"@3id/connect";import{EthereumAuthProvider: k}from"@3id/connect";import{Core: v}from"@self.id/core";import{DID: f}from"dids";var s=(t,e,r)=>{if(!e.has(t))throw TypeError("Cannot "+r)},d=(t,e,r)=>(s(t,e,"read from private field"),r?r.call(t):e.get(t)),w=(t,e,r)=>{if(e.has(t))throw TypeError("Cannot add the same private member more than once");e instanceof WeakSet?e.add(t):e.set(t,r)},p=(t,e,r,a)=>(s(t,e,"write to private field"),a?a.call(t,r):e.set(t,r),r),n;class o extends v{constructor(e){super(e);w(this,n,void 0),p(this,n,new l(e.connectNetwork??e.ceramic))}get threeId(){return d(this,n)}async authenticate(e,r=!0){const a=await this.connect(e);return await a.authenticate(),r&&(this.ceramic.did=a),a}async connect(e){return await d(this,n).connect(e),new f({provider:d(this,n).getDidProvider(),resolver:this.resolver})}}n=new WeakMap;var h=(t,e,r)=>{if(!e.has(t))throw TypeError("Cannot "+r)},c=(t,e,r)=>(h(t,e,"read from private field"),r?r.call(t):e.get(t)),_=(t,e,r)=>{if(e.has(t))throw TypeError("Cannot add the same private member more than once");e instanceof WeakSet?e.add(t):e.set(t,r)},D=(t,e,r,a)=>(h(t,e,"write to private field"),a?a.call(t,r):e.set(t,r),r),i;const u=class{constructor(t){if(_(this,i,void 0),!t.client.ceramic.did?.authenticated)throw new Error("Input DID must be authenticated, use SelfID.authenticate() instead of new SelfID()");D(this,i,t.client)}static async authenticate(t){const{authProvider:e,...r}=t,a=new o(r);return await a.authenticate(e,!0),new u({client:a})}get client(){return c(this,i)}get did(){const t=c(this,i).ceramic.did;if(t==null||!t.authenticated)throw new Error("Expected authenticated DID instance to be attached to Ceramic");return t}get id(){return this.did.id}async get(t){return await c(this,i).dataStore.get(t,this.did.id)}async set(t,e){return await c(this,i).dataStore.set(t,e)}async merge(t,e){return await c(this,i).dataStore.merge(t,e)}};let I=u;i=new WeakMap;export{k: EthereumAuthProvider,I: SelfID,o: WebClient} = pkg;
```

Also it seems that importing `@self.id/framework` requires adding `styled-components`.

This is just a newly generated Nextjs repo with `pages/_app.tsx` modified with `import { Provider } from "@self.id/framework"` and `<Provider />`

---

You can start editing the page by modifying `pages/index.tsx`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.ts`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
