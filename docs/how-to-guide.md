# How to Set Up Automated Code Deployment with DevFlow

**Time required:** 30 minutes  
**Skill level:** Intermediate  
**Prerequisites:** A GitHub account, a web application, admin access to your server

---

## Overview

This guide walks you through connecting your GitHub repository to DevFlow 
so that every time you push code, it automatically tests and deploys your 
application — no manual steps required.

By the end of this guide, you will have:

- Connected your GitHub repository to DevFlow
- Configured a build pipeline with automated tests
- Set up deployment to your staging environment

---

## Step 1: Connect Your Repository

1. Log in to [DevFlow](https://devflow.io) and click **New Pipeline**.
2. Select **GitHub** as your source.
3. Click **Authorize DevFlow** and sign in to GitHub when prompted.
4. From the repository list, select the repo you want to deploy.
5. Click **Connect**.

> **Note:** DevFlow requires at minimum **read access** to your repository 
> and **write access** to commit deployment status badges.

---

## Step 2: Configure Your Build Settings

Once connected, DevFlow detects your project type automatically. 
Verify the settings on the **Build Configuration** screen:

| Setting         | Recommended Value         | Notes                              |
|-----------------|---------------------------|------------------------------------|
| Build command   | `npm run build`           | Or your project's build command    |
| Test command    | `npm test`                | Pipeline fails if tests fail       |
| Node version    | 20.x                      | Matches your production environment|
| Branch to watch | `main`                    | Deploys only from your main branch |

Click **Save Configuration**.

---

## Step 3: Add Your Server Credentials

DevFlow needs SSH access to deploy to your server.

1. In DevFlow, go to **Settings → Deployment Targets**.
2. Click **Add Target**.
3. Enter your server details:
   - **Host:** Your server IP or domain (e.g., `deploy.yourapp.com`)
   - **Username:** Your deployment user (e.g., `deploy`)
   - **SSH Key:** Paste your private SSH key
4. Click **Test Connection** — you should see a green **Connected** status.
5. Click **Save Target**.

> ⚠️ **Security note:** Use a dedicated deployment user with limited 
> permissions — not your root or admin account.

---

## Step 4: Trigger Your First Deployment

1. Push any change to your `main` branch on GitHub:

````bash
git add .
git commit -m "Test DevFlow deployment"
git push origin main
````

2. Open DevFlow and click **Pipelines**. You'll see a new run in progress.
3. Click the run to watch the live log output.

A successful run looks like this:
---

## Troubleshooting

**Tests fail on the pipeline but pass locally**  
Your local environment may differ from the build environment. Check that your 
`package.json` lists all dependencies explicitly — none should be globally 
installed only on your local machine.

**"Permission denied" during deployment**  
Verify that your SSH key is added to the `authorized_keys` file on your server 
for the deployment user:

````bash
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
````

**Pipeline stuck on "Queued" for more than 5 minutes**  
DevFlow's free tier has limited concurrency. Check the status page at 
[status.devflow.io](https://status.devflow.io) for any ongoing incidents.

---

*This is a writing sample created for portfolio purposes. DevFlow is a fictional product.*
