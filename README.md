********************************************************
Straightforward Training(TM)
How to Publish in Github (no branches/single user)
Author: Saulo S. Ortiz
Date: 20180604
Update: 20200802
********************************************************

≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡
DISCLAIMER:
Not responsible for corrupt or loss of data. Steps have been verified multiple times.
≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡

1. Download the GitBash program
  • www.git-scm.com

2. Download the ATOM editor
  • https://atom.io/

3. Install both programs

4. Create a github account in github.com

5. In your computer create a Github folder to work from
  • create a subfolder for each subject you want

6. Login to github and create a new repository for the subject you want to push (upload)
  • an initial instructions page will show up

7. Go to the github folder in your computer and right click on it...select Git Bash here
from the list and a terminal screen will show...wait a few seconds for it to load

8. Run ATOM and from the menu select the github folder...
  • the folder and subfolders will show up
  • close all the initial tabs in ATOM

9. Go to GitBash and use it using Linux commands
  • cd, ls, rm, mkdir, touch

10. Now cd to the first subject you want to work with

11. Type git init to create a hidden folder that github needs

12. Type touch .gitignore to create the hidden .gitignore file

13. In ATOM double click the .gitignore file and in it type log.txt
  • this will tell gitgub NOT to push any log files to it
  • you can add different file names here for github NOT to receive when you do pushes

14. Type touch <your_file_name> which creates an empty file you are going to work from and push...in my
case mine reads instructions.txt

15. Using ATOM edit your file with the data you want in it...instructions, commands, etc

16. When you’re ready to push (upload) type git add .
  • This adds all the files in git that subfolder to the queue
  • You can also add single files using their format like .html or .txt, etc

17. Looking at the initial page in your github account copy and paste into gitbash the command:
  • git commit -m ‘first commit’
  • this commits your queue to upload and adds the comment ‘first commit’ for reference purposes

18. Now copy and paste into gitbash the long command in the repository page which links gitbash to the
repository you’re going to push to...a login screen pops up...log in.
  • i.e (git push https://github.com/ortizimo/Jailbreak-iPad-1st-Gen-2019.git)

19. Now you can use the last command git push -u origin master to upload your content
this command is used this one time as its a new repository after that you will use the following
commands do all your work:
  • git add .
  • git commit -m ‘your_comment’
  • git push <URL_to_Repository>
  or git push -f <URL_to_Repository>

****************************************************************************************
NOTE: Make sure you copy/paste the URL to the repository from your browser into Git Bash
****************************************************************************************

Additional Notes:
1. Refresh your repository and do any changes if the format looks off. Also, if you want to add a README
 file with some comments or instructions you need to type touch README.md then use ATOM to add what you
 want to say.

2. You need to do these steps for each new repository...updating any old repositories only uses the last
commands in step #19.

3. After login in you do not need to do it anymore unless you disconnect.

4. If you have any errors shut down both programs then restart them.

5. Once you log into your account through Git Bash all you have to do to update old repositories are the
commands below unless you create a new one...then you have to do all starting at step #10 above.
  • git add .
  • git commit -m ‘your_comment’
  • git push <URL_to_Repository>

****************************************************************************************
NOTE: if you need to overwrite then use force update:
  • git push -f <URL_to_Repository>
****************************************************************************************

6. If you have any errors or issues shut both programs off then restart them...if that doesn't work
then reboot.

7. You'll need to do these steps for EACH repository.

8. Any errors...shut everything off then redo.

9. You need to do these steps for each new repository...updating only uses the last commands above.
ands above.
