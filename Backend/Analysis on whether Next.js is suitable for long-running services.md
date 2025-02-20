# Analysis on whether Next.js is suitable for long-running services

## Deploying a Next.js service on Vercel

-   Next.js on Vercel uses Serverless runtime by default, where a new instance is created for each request and destroyed after execution.

-   Vercel Serverless functions have a timeout: they cannot exceed 60 seconds on the Pro plan and 5 seconds on the free plan.

-   Memory and resource limits: Vercel automatically shuts down idle functions.

-   If you deploy Next.js on Vercel, this means you cannot run long-running processes that maintain persistent connections (such as WebSocket servers, queue consumers, or scheduled tasks) within Next.js API Routes.

## Self-hosted Next.js server

-   A self-hosted Next.js server can run long-running services such as WebSocket servers, queue consumers, and scheduled tasks.
-   Since you have full control over the server environment, you can avoid the Serverless limitations of Vercel. As a result, long-running processes can continue running on a self-hosted server without being destroyed or timing out.

## Suggestion

-   If your application requires long-running processes (such as WebSocket servers, subscription listeners, background tasks, etc.), it is recommended to use a traditional Node.js server rather than Serverless.
