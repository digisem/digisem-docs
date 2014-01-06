Screenshots
============

<h4>Create a new digisem</h4>
<p>1. Activate the edit mode in the course room and add a new activity module of type digisem:</p>
![Wizard to create a new module](/imgs/create-wizard.png "Wizard to create a new module")
<hr>
<p>2. Insert the name of the module (which is displayed in the course room) and navigate to the library catalogue (OPAC). </p>
![First step to create a new digisem module](/imgs/create-name-and-forward.png "First step to create a new digisem module")
<hr>
<p>3. The library catalogue (OPAC) needs to redirect you back to moodle (/mod/digisem/bridge.php) with the book information as HTTP request parameters. These are shown in the form: </p>
![Alter the book information which is then sent to the library](/imgs/create-return-from-opac.png "Library information in the digisem module form")
<hr>
<p>If you click on submit, the plugin sends the scan request email to the library. This email contains all the necessary information to scan the correct book or article and then place the file (e.g. as PDF) on the shared FTP server. The module will fetch the file and integrate it into the course room automatically. </p>
<h4>Manage the digisem in the course room</h4>
![Manage the digisem](/imgs/list-view.png "Manage them digisem module")
<p>If you want, you can for instance move the digisem module into another week, hide it or remove it completely from the course room. </p>
<h4>Customize the Digisem plugin</h4>
<p>Administrators can edit the displayed configuration:</p>
![FTP config](/imgs/config-ftp.png "FTP config")
![Mail config](/imgs/config-mail.png "Mail config")
