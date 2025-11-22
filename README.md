# foundry-cheatsheet

## :beginner: Introduction
A lightweight starter repository for learning and experimenting with Foundry, a blazing-fast, portable, and modular toolkit for Ethereum development. This project includes setup guides, example contracts, and test scripts to help you quickly build and test smart contracts using Forge and Cast. 

This repository is still under development — updates and improvements are ongoing. (links below are temporary)

## :blue_book: Getting Started

It is strongly recommended to configure your author name and email. Failure to do so may result in an error message stating “No such file or directory.”

<details>
<summary>
  Configuration Guide
</summary> <br />

```bash
# check if the git configuration file has been initialized 
$ git config --global --list

# initialize git configuration file
$ git config --global user.name "<your name>"
$ git config --global user.email "<your email>"

$ vi ~/.gitconfig
$ cat ~/.gitconfig
```
 
</details>

<details>
<summary>
  Directory creation
</summary> <br />

```bash
# check if the git configuration file has been initialized 
$ git config --global --list

# initialize git configuration file
$ git config --global user.name "<your name>"
$ git config --global user.email "<your email>"

$ vi ~/.gitconfig
$ cat ~/.gitconfig
```
 
</details>

<details>
<summary>
 Init
</summary> <br />

```bash
# check if the git configuration file has been initialized 
$ git config --global --list

# initialize git configuration file
$ git config --global user.name "<your name>"
$ git config --global user.email "<your email>"

$ vi ~/.gitconfig
$ cat ~/.gitconfig
```
 
</details>

<details>
<summary>
  Compile
</summary> <br />

```bash
# check if the git configuration file has been initialized 
$ git config --global --list

# initialize git configuration file
$ git config --global user.name "<your name>"
$ git config --global user.email "<your email>"

$ vi ~/.gitconfig
$ cat ~/.gitconfig
```
 
</details>

<details>
<summary>
  Clean up
</summary> <br />

```bash
# check if the git configuration file has been initialized 
$ git config --global --list

# initialize git configuration file
$ git config --global user.name "<your name>"
$ git config --global user.email "<your email>"

$ vi ~/.gitconfig
$ cat ~/.gitconfig
```
 
</details>


## :hammer_and_wrench: Installation

### Foundry Installation

Suitable for applications that have their own bundler and send the JS bundle
directly to a client (without publishing it to npm). Think of a user-facing app
or website, like an email client, a CRM, a landing page or a blog with
interactive elements, using React/Vue/Svelte lib or vanilla JS.

<details><summary><b>Show instructions</b></summary>

1. Install the preset:

    ```sh
    npm install --save-dev size-limit @size-limit/file
    ```

2. Add the `size-limit` section and the `size` script to your `package.json`:

    ```diff
    + "size-limit": [
    +   {
    +     "path": "dist/app-*.js"
    +   }
    + ],
      "scripts": {
        "build": "webpack ./webpack.config.js",
    +   "size": "npm run build && size-limit",
        "test": "vitest && eslint ."
      }
    ```

3. Here’s how you can get the size for your current project:

    ```sh
    $ npm run size

      Package size: 30.08 kB with all dependencies, minified and brotlied
    ```

4. Now, let’s set the limit. Add 25% to the current total size and use that as
   the limit in your `package.json`:

    ```diff
      "size-limit": [
        {
    +     "limit": "35 kB",
          "path": "dist/app-*.js"
        }
      ],
    ```

5. Add the `size` script to your test suite:

    ```diff
      "scripts": {
        "build": "webpack ./webpack.config.js",
        "size": "npm run build && size-limit",
    -   "test": "vitest && eslint ."
    +   "test": "vitest && eslint . && npm run size"
      }
    ```

6. If you don’t have a continuous integration service running, don’t forget
   to add one — start with Github Actions.

</details>


### Installing dependencies

File size limit (in kB) is not the best way to describe your JS application
cost for developers. Developers will compare the size of the JS bundle
with the size of images. But browsers need much more time to parse 100 kB
of JS than 100 kB of an image since JS compilers are very complex.

This is why Size Limit support time-based limit. It runs headless Chrome
to track the time a browser takes to compile and execute your JS.

<details><summary><b>Show instructions</b></summary>

1. Install the preset:

    ```sh
    npm install --save-dev size-limit @size-limit/preset-app
    ```

2. Add the `size-limit` section and the `size` script to your `package.json`:

    ```diff
    + "size-limit": [
    +   {
    +     "path": "dist/app-*.js"
    +   }
    + ],
      "scripts": {
        "build": "webpack ./webpack.config.js",
    +   "size": "npm run build && size-limit",
        "test": "vitest && eslint ."
      }
    ```

3. Here’s how you can get the size for your current project:

    ```sh
    $ npm run size

      Package size: 30.08 kB with all dependencies, minified and brotlied
      Loading time: 602 ms   on slow 3G
      Running time: 214 ms   on Snapdragon 410
      Total time:   815 ms
    ```

4. Now, let’s set the limit. Add 25% to the current total time and use that as
   the limit in your `package.json`:

    ```diff
      "size-limit": [
        {
    +     "limit": "1 s",
          "path": "dist/app-*.js"
        }
      ],
    ```

5. Add the `size` script to your test suite:

    ```diff
      "scripts": {
        "build": "webpack ./webpack.config.js",
        "size": "npm run build && size-limit",
    -   "test": "vitest && eslint ."
    +   "test": "vitest && eslint . && npm run size"
      }
    ```

6. If you don’t have a continuous integration service running, don’t forget
   to add one — start with Github Actions.

</details>


## :atom: Deploy

It's highly recommended to configure the author name and email.  
You will get an error "No such file or directory" 

<details>
<summary>
  Deploy a smart contract locally
</summary> <br />

```bash
#
$ cd ~
$ pwd

# set up our command prompt so that we can again can see written to set up our command using git 
$ curl -O https://raw/githubusercintent.com/git/git/master/contrib/completion/git-prompt.sh
 
# add a command to a particular file so everytime we start this git bash shell, the script that we downloaded is run. This command opens the batch file:
$ vi .bashrc
then press I, and start typing
then type the following:

. ~/git-prompt.sh
export GIT_PS1_SHOWDIRTYSTATE=1
export PS1='[\u@\h \W$(__git_ps1 " (%s)")]\$ '

press colon, then type x
press ENTER 

$ cat .bashrc
$ exit 

# Reopen git bash. It will show that it has been configured correctly if you see :
- user name
- host name
- current directory
- git branch name
- repo status indicator
- end in $
```

```bash
# set Path
Windows:
1.Find the Git installation path: This is typically C:/Program Files/Git/bin and C:/Program Files/Git/cmd. Verify this on your system.
2.Search for "environment variables": Open the Start menu, type "environment variables," and select "Edit the system environment variables."
3.Open Environment Variables: In the System Properties window, click the "Environment Variables..." button.
4.Edit Path variable:•Under "User variables" (for the current user) or "System variables" (for all users), find the variable named Path and select it.•Click "Edit...".
5.Add Git paths:
• Click "New" and add the path to your Git bin directory (e.g., C:/Program Files/Git/bin).
• Click "New" again and add the path to your Git cmd directory (e.g., C:/Program Files/Git/cmd). 
```

```bash
$ git --version
```

```bash
# gitignore

# Dotenv file
.env
broadcast/
lib/
```

</details>

<details>
<summary>
  Deploy a smart contract locally using Anvil
</summary> <br />

```bash
# 
$ 
```
</details>

<details>
<summary>
  SUMMARY of Deployment to PROD with real money
</summary> <br />

```bash
#  
$ cd ~
$ pwd

# download this file to configure the command prompt
$ curl -O https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
$ vi .bashrc
then press I, and get to the bottom of the file
then type the following:

. ~/git-prompt.sh + press ENTER, type the following:
export GIT_PS1_SHOWDIRTYSTATE=1
export PS1='[\u@\h \W$(__git_ps1 " (%s)")]\$ '

press ENTER then ESC
type :x + press ENTER. This means it is saved.

$ cat .bashrc
$ exit
```
 
</details>

## :pencil2: Coding

It's highly recommended to configure the author name and email.  
You will get an error "No such file or directory" 

<details>
<summary>
  Deploy a smart contract locally
</summary> <br />

```bash
#
$ cd ~
$ pwd

# set up our command prompt so that we can again can see written to set up our command using git 
$ curl -O https://raw/githubusercintent.com/git/git/master/contrib/completion/git-prompt.sh
 
# add a command to a particular file so everytime we start this git bash shell, the script that we downloaded is run. This command opens the batch file:
$ vi .bashrc
then press I, and start typing
then type the following:

. ~/git-prompt.sh
export GIT_PS1_SHOWDIRTYSTATE=1
export PS1='[\u@\h \W$(__git_ps1 " (%s)")]\$ '

press colon, then type x
press ENTER 

$ cat .bashrc
$ exit 

# Reopen git bash. It will show that it has been configured correctly if you see :
- user name
- host name
- current directory
- git branch name
- repo status indicator
- end in $
```

```bash
# set Path
Windows:
1.Find the Git installation path: This is typically C:/Program Files/Git/bin and C:/Program Files/Git/cmd. Verify this on your system.
2.Search for "environment variables": Open the Start menu, type "environment variables," and select "Edit the system environment variables."
3.Open Environment Variables: In the System Properties window, click the "Environment Variables..." button.
4.Edit Path variable:•Under "User variables" (for the current user) or "System variables" (for all users), find the variable named Path and select it.•Click "Edit...".
5.Add Git paths:
• Click "New" and add the path to your Git bin directory (e.g., C:/Program Files/Git/bin).
• Click "New" again and add the path to your Git cmd directory (e.g., C:/Program Files/Git/cmd). 
```

```bash
$ git --version
```

```bash
# gitignore

# Dotenv file
.env
broadcast/
lib/
```

</details>

<details>
<summary>
  Deploy a smart contract locally using Anvil
</summary> <br />

```bash
# 
$ 
```
</details>

<details>
<summary>
  SUMMARY of Deployment to PROD with real money
</summary> <br />

```bash
#  
$ cd ~
$ pwd

# download this file to configure the command prompt
$ curl -O https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
$ vi .bashrc
then press I, and get to the bottom of the file
then type the following:

. ~/git-prompt.sh + press ENTER, type the following:
export GIT_PS1_SHOWDIRTYSTATE=1
export PS1='[\u@\h \W$(__git_ps1 " (%s)")]\$ '

press ENTER then ESC
type :x + press ENTER. This means it is saved.

$ cat .bashrc
$ exit
```
 
</details>



## :jigsaw: TESTNET
You can clone a remote repository from a remote server. For example from Github to your local machine. Github is arguably the most popular web based Git repository hosting service in the world.

<details>
<summary>
SEPOLIA with .env 
</summary> <br />

```bash
# 
$ cd <main-directory-name>
<main-directory-name> $ ls

# copy the downloaded into this main-directory-name
<main-directory-name> $ cp <location of the zip file> 
<main-directory-name> $ ls -al
<main-directory-name> $ unzip <type the first 3 letters of the file and press TAB>
<main-directory-name> $ ls  (you will see sortedCollections)
<main-directory-name> $ ls -al
<main-directory-name> $ rm <type the first 3 letters of the file and press TAB>
<main-directory-name> $ ls -al (the zip file has been removed.)
<main-directory-name> $ clear

# rename sortedCollections
<main-directory-name> $ mv sortedCollections/ converted-git-repo
<main-directory-name> $ ls -al
<main-directory-name> $ cd converted-git-repo

# your are now in converted-git-repo directory
<converted-git-repo> $ ls -l
<converted-git-repo> $ cd src (optional)
<converted-git-repo> $ git init (creates an empty repository)
 
```
 
</details>




<details>
<summary>
SEPOLIA without .env 
</summary> <br />

- **Step 1**: Provide "Repository name" for example 'git-bootcamp'
- **Step 2**: Add Description (optional)
- **Step 3**: Select Public or Private
- **Step 4**: Initialize this repository with: tick "Add a README file"
- **Step 5**: add .gitignore (optional)
- **Step 6**: Add a license (optional)
- **Step 7**: click "Create repository" 
- **Step 8**: copy the remote repository URL
> [!see this]
> HTTPS or SSH : https://github.com/lpadlan/git-bootcamp.git.
 
</details>


## :test_tube: Tests

<details>
    <summary>Unit Tests</summary>

### Unit Tests

To unit-test an event-sourced aggregate, it's to verify that the Aggregate produces the expected event as output given a specific set of input Events and a Command. This involves creating an Aggregate
instance, applying the input events to it, handling the command, and verifying the expected event output.

```csharp
[Fact]
public void CreateCartShouldRaiseCartCreated()
    => Given<ShoppingCart>()
        .When<Command.CreateCart>(new(_cartId, _customerId))
        .Then<DomainEvent.CartCreated>(
            @event => @event.CartId.Should().Be(_cartId),
            @event => @event.CustomerId.Should().Be(_customerId),
            @event => @event.Status.Should().Be(CartStatus.Active));
```

</details>

<details>
    <summary>Integration Tests</summary>

### Integration Tests

// TODO

</details>

<details>
    <summary>Load Tests</summary>

### Load Testing (K6)

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```

</details>

## :book: References

### Projects

- [xxx](https://github.com/xxxx)

### Training 

- [Cyfrin Updraft](https://updraft.cyfrin.io/)
- [Ethereum development documentation](https://ethereum.org/developers/docs/)


### Articles

- [xxx](https://www.xxx.org/)
-  

### Blogs

- [xxx](https://blogsxxx/) 

### Posts

- [XXX](https://www.xxxxx.com/articles/) 


## :toolbox: Tech Stack
### API
- [OpenZeppelin](https://www.openzeppelin.com/) - Its bedrock open source Contract Libraries are a public good and industry standard for smart contract development

### ChainIDs
- [Chainlist](https://chainlist.org/) - ChainList is a list of EVM networks
  - [hello]
  
### Oracle
- [Chainlink](https://dev.chain.link/) - A free, cross-platform and open-source web-development framework;

### Transactions
- [Etherscan](https://etherscan.io/)
  - [Ethereum Gas Tracker](https://etherscan.io/gastracker)
  - [Ethereum Unit Converter](https://www.alchemy.com/gwei-calculator)         
- [Metamask](https://metamask.io/)
  - [Sepolia TestNet](https://etherscan.io/gastracker)
  - [Tenderly Virtual Signup](https://tenderly.co/?mtm_campaign=partner&mtm_kwd=cyfrin)     
 
## Authors

> See the list of [contributors](https://github.com/contributorsxxx) who participated in this project.

## License

This project is licensed under the **MIT license**. Feel free to edit and distribute this template as you like.

See [LICENSE](LICENSE) for more information.

## Courses Code References

Thanks for these awesome resources that were used during this training: 

- <https://github.com/Cyfrin/blockchain-basics-cu>
- <https://github.github.com/gfm/>
- <https://tom.preston-werner.com/2010/08/23/readme-driven-development.html>

 
## Contributors

 
 
