# How I built my site 

10/12/2022

Previously I used [Wix](https://www.wix.com/), however, it wasn't the result I was looking for so I decided to rebuild my portfolio using [MkDocs](https://www.mkdocs.org), [GitHub](https://github.com/), and [GitPages](https://pages.github.com/).

If you would like to build a similar website then the next section includes a guide on how I did it. 

## Install Python and MkDocs

If you have Python installed already then you can skip this step. If not you can [download and install the latest release](https://www.python.org/downloads/) from their website.

Then install MkDocs through the command line by running:

    pip install mkdocs

## Create a new project

Create a project by running the following command in the command line: 

    mkdocs new project

Change to your project directory using the `cd` command:

    cd project

Check you have a folder named `project` that contains; a `docs` folder and two files `mkdocs.yml`, and `index.md`.

For more details on these files see the MkDocs [Getting Started](https://www.mkdocs.org/getting-started/) guide. 

## Preview your site

You can preview your site by running the `mkdocs serve` command: 

    mkdocs serve

This will launch a local version of your site that you can view by going to http://127.0.0.1:8000/ in your browser.

## Build it

Now you've had a look we can go ahead and build your site by running the `mkdocs build` command;

    mkdocs build

This will create a new folder named `site` that includes everything you need for a static website. 

## Host your site with GitHub and GitPages

If you haven't already, [create a GitHub repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository) for your website. 

Run the next command to make sure your `/site` folder is ignored by GitHub.

    echo "site/" >> .gitignore

Then add your local MkDocs site to GitHub by running the following commands:

    git init
    git add .
    git commit -m "First commit"
    git remote add origin <REMOTE_URL>
    git push -u origin main

The `<REMOTE_URL>` needs to be replaced with the URL of your repository.

Lastly, run the `mkdocs gh-deploy` command:

    mkdocs gh-deploy

MkDocs will commit and push the local site to your GitHub repository, and your website will be live on GitPages.

The URL for your site will look similar to mine, <https://connor-partington.github.io/portfolio/>, but it will include your GitHub username and project name instead. 