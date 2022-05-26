This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.js`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

## Sequence diagrams

```mermaid-example
sequenceDiagram
		%% par = Parallel（並列処理）
    par Authentication Request
        ユーザー ->> フロントエンド: ログイン
    and Authentication Reponse
        フロントエンド -->> ユーザー: 認証  
    end
    par File Upload Request
        ユーザー ->> API: 画像のアップロード/上書/取消
				par File Id Regist Request
            API ->> RDB : ファイルIDの登録/更新/削除
						API ->> AWS S3 : ファイルの登録/更新/削除
        and File Id Regist Request
            RDB -->> ユーザー: RDB更新結果
						AWS S3 -->> ユーザー : AWS S3更新結果
				end
    end
```