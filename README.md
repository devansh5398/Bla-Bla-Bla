# Codeforces-Questions-Scraper

### Deployable Flask app that uses
* **BeautifulSoup** and **Requests** libraries to scrape Codeforces problemset's problem statements, and
* **pdfkit** library to save them into pdf format.

### How it works
* App scrapes problems list on the basis of input page number.
* One can select problems from scraped problems list to download their statements into pdf format.

### Steps to deploy on Heroku (using Heroku CLI)
* Create an app on Heroku
* Firstly create a file with name **`.buildpacks`** which will help in installing wkhtmltopdf on Heroku. File will contain:

  ```
  https://github.com/heroku/heroku-buildpack-apt
  https://github.com/chap/wkhtmltopdf-heroku-18-buildpack
  ```
* Initialize git using `git init`
* Add these necessary files using `git add filename`
  * static/app_script.js
  * templates/index.html
  * main.py
  * Procfile
  * requirements.txt
  * .buildpacks
  * Aptfile
* Commit these changes as `git commit -m "add description"`
* Login to your Heroku account: `heroku login -i`
* Connect to your app on Heroku: `heroku git:remote -a <your app name>`
* To install all the buildpacks present in **.buildpacks**, we need to use [heroku-buildpack-multi](https://github.com/heroku/heroku-buildpack-multi):
  ```
  heroku buildpacks:set https://github.com/heroku/heroku-buildpack-multi.git
  ```
* Then push your commits: `git push heroku master`

### References
Main hurdle in deploying this first project on Web Scraping was how to use wkhtmltopdf on Heroku. Thanks to these webpages which helped me a lot:
* https://github.com/pdfkit/pdfkit/wiki/Use-with-Heroku
* https://elements.heroku.com/buildpacks/chap/wkhtmltopdf-heroku-18-buildpack
* https://github.com/heroku/heroku-buildpack-apt
* https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app
* https://elements.heroku.com/buildpacks/jazzcore/python-pdfkit
* https://help.heroku.com/IYRYW6VB/how-do-i-install-additional-software-packages-that-my-application-requires
* https://wkhtmltopdf.org/downloads.html
* https://stackoverflow.com/questions/38924458/how-to-see-files-and-file-structure-on-a-deployed-heroku-app
