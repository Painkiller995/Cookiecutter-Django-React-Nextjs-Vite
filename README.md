# Cookiecutter Django React NextJS/Vite

🍪❤️ A Refreshing Twist on Cookiecutter Django 🍪❤️

Cookiecutter-Django-React-Nextjs-Vite empowers you to rapidly kickstart production-ready Django projects with a frontend, all thanks to the magic of Cookiecutter. Drawing significant inspiration from [cookiecutter-django](https://github.com/cookiecutter/cookiecutter-django).

Documentation: Work in Progress - Your Contributions are Welcome! 📚

Encountering issues with Cookiecutter Django? Don't hesitate to [open an issue](https://github.com/Painkiller995/Cookiecutter-Django-React-Nextjs-Vite/issues).

## Features

- 🚀 Frontend and Backend - Separated but United

### Backend

- Django 4.2 takes center stage 🎭
- Powered by Python 3.11 magic 🐍✨
- Adheres to the 12-Factor app principles using `django-environ` ⚙️
- Embraces a security-first approach with SSL 🛡️
- Fine-tuned settings for both development and production environments 🛠️
- Efficient media storage utilizing nginx 📦
- Docker: Your companion for seamless development and production (Traefik and LetsEncrypt support) 🐳
- Flexibility galore: Tailor your PostgreSQL version 🐘
- Optionally serves static files via Whitenoise (Optional) 🌐
- Supports Celery and Flower configurations (Optional) 🌸
- Django Rest Framework (Optional): Easily integrate a powerful API framework for building Web APIs 🌐

### Frontend

- Powered by React️
- Production-mode frontend served by Nginx 🖥️
- Dev environment prepped with Vite and TypeScript for instant action 🛠️
- Optimal production build for a smooth launch 🚀
- Built-in linting and code formatting powered by ESLint and Prettier 🧹
- Seamlessly integrates with popular testing libraries 🧪
- User-friendly scripts to launch your dev server and build your project 🏗️

## Usage

1. Install Cookiecutter (if not already installed):

   ```bash
   pip install "cookiecutter>=1.7.0"
   ```

2. Generate your project using Cookiecutter-Django-React-Nextjs-Vite:

   ```bash
   cookiecutter https://github.com/Painkiller995/Cookiecutter-Django-React-Nextjs-Vite
   ```

3. Follow the prompts to provide your project details.

4. After generating the project, navigate into the project directory:

   ```bash
   cd yourprojectname/
   ```

5. If you are using **Next.js**:

   ```bash
   npx create-next-app@latest ./frontend
   ```

   Configure hot-reloading by adding the following to your `next.config.js` file:

   ```javascript
   // next.config.js
   /** @type {import('next').NextConfig} */
   const nextConfig = { output: "standalone" };

   export default nextConfig;
   ```

   If you're on Windows, ensure proper hot-reloading by adding the following to your `local.yml` file:

   ```yaml
   # local.yml
   environment:
     - WATCHPACK_POLLING=true
   ```

   If you are using **Vite**:

   ```bash
   npm create vite@latest ./frontend
   ```

   ```javascript
   // vite.config.ts
   import { defineConfig } from "vite";
   import react from "@vitejs/plugin-react";

   // https://vitejs.dev/config/
   export default defineConfig({
     plugins: [react()],
     server: {
       host: true,
       port: 3000, // This is the port which we will use in docker
       // add the next lines if you're using windows and hot reload doesn't work
       watch: {
         usePolling: true,
       },
     },
   });
   ```

   Follow the prompts to set up your frontend project.

6. Initialize a Git repository, add your code, and push to your chosen remote:

   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin git@github.com:yourusername/yourprojectname.git
   git push -u origin main
   ```

For local development and deployment instructions, refer to:

- [Developing Locally using Docker](https://cookiecutter-django.readthedocs.io/en/latest/developing-locally-docker.html) (based on django-cookiecutter documentation)

## Frontend and Backend Routes🌐

By default, this project is configured with the following routes:

- Accessing the root URL ("/") will direct you to the frontend.
- Accessing "/services" will direct you to the backend.

Feel free to customize these routes based on your project requirements.

## Next.js Kick Start Template 🚀

Looking for a customizable Next.js template with authentication pages, custom layouts, dark mode, and more? Check out [Shadcn/ui - Next.js Template](https://github.com/Painkiller995/Shadcnui-Next.js-Template). Integrate it seamlessly with this project for a powerful full-stack development experience.

## Not a React developer? 🚫

If you're not working with React, no worries! The frontend is separated and not tightly coupled to the backend. Feel free to delete the content of the frontend folder and use your favorite Vite template. Just make sure to use the same commands in the package.json file for "dev" and "build".

## What's on the Horizon 🔮

- Incorporating django-allauth/Djoser (Optional Feature) 🔐

## License 📄

This project is governed by the terms and conditions specified in the [License](LICENSE) file.

**Project Visitors**

![Project Visitors](https://profile-counter.glitch.me/Cookiecutter-Django-React-Nextjs-Vite/count.svg)
