# Svelte example demo CI/CD pipeline

<a href="https://dash.elest.io/deploy?source=cicd&social=Github&url=https://github.com/elestio-examples/svelte"><img src="src\assets\deploy-on-elestio.png" alt="Deploy on Elest.io" width="180px" /></a>


```
npm init vite Project-name -- --template svelte
```
# Svelte + Vite

This template should help get you started developing with Svelte in Vite.

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode).

## Need an official Svelte framework?

Check out [SvelteKit](https://github.com/sveltejs/kit#readme), which is also powered by Vite. Deploy anywhere with its serverless-first approach and adapt to various platforms, with out of the box support for TypeScript, SCSS, and Less, and easily-added support for mdsvex, GraphQL, PostCSS, Tailwind CSS, and more.

## Technical considerations

**Why use this over SvelteKit?**

- It brings its own routing solution which might not be preferable for some users.
- It is first and foremost a framework that just happens to use Vite under the hood, not a Vite app.
  `vite dev` and `vite build` wouldn't work in a SvelteKit environment, for example.

This template contains as little as possible to get started with Vite + Svelte, while taking into account the developer experience with regards to HMR and intellisense. It demonstrates capabilities on par with the other `create-vite` templates and is a good starting point for beginners dipping their toes into a Vite + Svelte project.

Should you later need the extended capabilities and extensibility provided by SvelteKit, the template has been structured similarly to SvelteKit so that it is easy to migrate.

**Why `global.d.ts` instead of `compilerOptions.types` inside `jsconfig.json` or `tsconfig.json`?**

Setting `compilerOptions.types` shuts out all other types not explicitly listed in the configuration. Using triple-slash references keeps the default TypeScript setting of accepting type information from the entire workspace, while also adding `svelte` and `vite/client` type information.

**Why include `.vscode/extensions.json`?**

Other templates indirectly recommend extensions via the README, but this file allows VS Code to prompt the user to install the recommended extension upon opening the project.

**Why enable `checkJs` in the JS template?**

It is likely that most cases of changing variable types in runtime are likely to be accidental, rather than deliberate. This provides advanced typechecking out of the box. Should you like to take advantage of the dynamically-typed nature of JavaScript, it is trivial to change the configuration.

**Why is HMR not preserving my local component state?**

HMR state preservation comes with a number of gotchas! It has been disabled by default in both `svelte-hmr` and `@sveltejs/vite-plugin-svelte` due to its often surprising behavior. You can read the details [here](https://github.com/rixo/svelte-hmr#svelte-hmr).

If you have state that's important to retain within a component, consider creating an external store which would not be replaced by HMR.

```js
// store.js
// An extremely simple external store
import { writable } from 'svelte/store'
export default writable(0)
```


<img src="src\assets\svelteScreenshot.png" alt="screenshot of the example app" width="100%" />


## CI/CD on Elestio

Showing here how to deploy to Elestio.

# Steps to create CI/CD pipeline on elestio

### Step 1: Select CI/CD from left sidebar in app.

Click [here](https://dash.elest.io/deploy?source=cicd) to directly go to the CI/CD

### Step 2: Select Deployment method.

We have three different types of deployment method

- Github
- Gitlab
- Docker compose

But for this svelte Template, you can choose GitHub as your deployment method.

### Step 3: Authentication

Select Clone in step at step Git Repository and select svelte template for creating a repository in your git account after that authenticate with Git by clicking on
Continue with Github button and authorize elestio to access git then you can rename you repository name if you want.

Else If you forked the repo then you can click on the Continue with GitHub button and authorize elestio to access the git repo then you can select the svelte repo otherwise you can directly insert a git repo URL to deploy the svelte application.

### Step 4: Configuration

After selecting a repo or inserting a URL it will auto-filled all the desired configurations using the elestio.yml/elestio.json file.

You can also manually customize the Configure your application. 

Select your runtime and its version, run & build commands.

Reverse proxy configuration, Volume Configuration, Exposed Ports Configuration and Environment variables.

### Step 5: Choose Deployment Targets

Elestio provides two different types of deployment targets.

- New Infrastructure
- Existing Infrastructures

On elestio single CI/CD target you can deploy multiple CI/CD pipelines so, If you already have CI/CD target on elestio then you can deploy a new pipeline on the same existing CI/CD target by choosing **Existing Infrastructures** and then select the CI/CD target otherwise if you don't have anything or want to deploy on new target then you can choose **New Infrastructure**

If you choose **New Infrastructure** then you have to select the deployment mode we have two different types of deployment modes.

- Single-mode.
- Cluster mode.

  **NOTE:-** Steps 6,7,8 and 9 are only for New Infrastructure targets for Existing Infrastructures targets directly following the final step.

### Step 6: Select Service Cloud Provider

Elestio supports five different types of cloud service providers you can choose anyone to deploy your service.

- Hetzner Cloud.
- Digital Ocean.
- Amazon Lightsail.
- Linode.
- Vultr.

We also provide a BYOVM service option so if you already have your VM on any third-party provider (Azure, GCP, Alibaba, ...) then you can choose BYOVM to deploy CI/CD pipeline on your VM.

Elestio provides one BYOVM service for free. To be eligible the VM you connect must have no more than 2 vCPU, max 4 GB of ram, and max 80 GB of storage

### Step 7: Select Service Plan

This step is only for other than BYOVM service providers.

We're providing multiple different types of service plans as per proposing by your selected providers.

### Step 8: Provide Service Name

By default, we create a unique target name for you but you can customize it.

### Step Final: Create Ci/CD pipeline

Now after following all the above steps you can click on the button **Create Ci/CD pipeline**.

It will take a few seconds to deploy your pipeline on elestio.

For each pipeline deployed on elestio will create a cname for it. but if you want your custom domain then you can configure it inside the target details.

After Pipeline is deployed you can able to view the app by visiting the pipeline domain.
