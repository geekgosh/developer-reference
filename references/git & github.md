Git
===
1.) git init
2.) git status
3.) git add -A | git add .
4.) git commit -m "Commit Message"
5.) git push
6.) git checkout -- . <<< back to previous commit
7.) git pull origin master <<< get the latest commit version of the repo
8.) git clone [repo .git]
9.) git remote -v <<< check current repo origin 
10.) git remote set-url origin [repo .git] <<< set new origin for repo
11.) git push origin master
12.) git log 
13.) git show <show last comment>
14.) git reset <file_name> <<< discard from latest git add
15.) git checkout -- <file_name> <<< change the file content to last commit
16.) git mv <original_file_name> <new_file_name>
17.) git rm <file_name_to_be_removed>
18.) git diff 
19.) git merge <branch_name_that_merge_to_current_branch> <<< fast-forward merge(when no conflict)
20.) git brand -d <branch_name> <<< delete branch
21.) git mergetool
22.) git tag <tag_name>
23.) git tag --list
24.) git stash, then git stash <stash_name> <<< apply and drop last stash
25.) git version
26.) git fetch || --all <<< update branch from remove
27.) git pull <<< update branch and update local file too

git config --global user.name "Name"
git config --global user.email "youremail@address.com"
^^^ setup git info to let it know who is commit the repo

Git Branch
----------
> git branch || -a <<< list all the branches for the repo, the repo with * is the current working repo
> git branch [branch name] <<< create new branch
> git checkout [branch name] <<< switch to branch, after git commit, you can freely switch between branch to modify it
> git checkout [master branch name], > git merge [branch to merge with master] <<< merge branch with master
> git push origin [branch name]
> git branch -d [branch name] <<< delete repo branch
> git checkout -b [branch name] <<< create branch and switch over it

Issues
======
1. Create issue in github
2. Can close by GUI in github, or terminal, where git commit -m "<message>, close <tag_id>" and push, github will auto detect and close the issue


Heroku
======
1. Go to heroku and create your new app
2. Download heroku cli
3. heroku logingit 
4. heroku keys:add (found key, than press 'Y')
5. heroku keys <<< view all keys
6. heroku keys.:remove <<< to remove key
7. ssh -v git@heroku.com <<< connect with heroku server

8. in your project
const port = process.env.PORT || 3000;
app.listen(port, () => {
	console.log(`Server is up on port ${port}`);
}); // so it can run at server otherwise local
9. package.json > scripts <<< is to specify the file to run intially
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node server.js"
}
  "engines": {
    "node": "8.5.0"
  },

10. npm start <<< to run the scripts > "start"
11. heroku create
12. git push heroku || git push heroku master
13. heroku open <<< view the output in heroku server
14. heroku logs <<< view log

HEROKU MONGODB
==============
AFTER heroku create
heroku addons:create mongolab:sandbox
heroku config <<< view mongodb link
mongoose.connect(process.env.MONGODB_URO || 'mongodb://localhost:27017/TodoApp');

heroku config:set NAME=SHENC
heroku config:get NAME
heroku config:unset NAME

heroku config:get MONGODB_URI
mongodb://heroku_w11x9pk4:rasbe0o0tl4vs40tovfdii2ldt@ds141534.mlab.com:41534/heroku_w11x9pk4
Protocol://username:password@address:PORT/DATABASE
When All Set
============
1. git status
2. git add .
3. git commit -m "commit message" 
4. git push
5. git push heroku