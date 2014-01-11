Screenshots
============

<h2>Create a new digisem</h2>
<p><strong>1.</strong> Activate the edit mode in the course room and add a new activity module of type digisem. According the language settings in moodle the module will be displayed as "Digitaler Semesterapparat" or "Digital Course Reserve":</p>
![Wizard to create a new module](/imgs/create-wizard.png "Wizard to create a new module")
<hr>
<p><strong>2.</strong> Insert the name of the module (which will be used as filename for the digital copy and displayed in the course room) and navigate to the library catalogue (OPAC) to get the item's metadata.</p>
![First step to create a new digisem module](/imgs/create-name-and-forward.png "First step to create a new digisem module")
<hr>
<p><strong>3.</strong> The library catalogue (OPAC) needs to redirect you back to moodle (/mod/digisem/bridge.php) with the book information as HTTP request parameters. These are shown in the form: </p>
![Alter the book information which is then sent to the library](/imgs/create-return-from-opac.png "Library information in the digisem module form")
<hr>
<p>If you click on submit, the plugin sends the scan request email to the library. This email contains all the necessary information to scan the correct book or article. The library system is responsible to place the resulting file of the scan (e.g. a PDF) on the FTP share. The Digisem plugin will fetch the file and integrate it into the course room automatically. </p>
<h2>Manage the digisem in the course room</h2>
![Manage the digisem](/imgs/list-view.png "Manage them digisem module")
<p>Each digisem module can be moved into another week of the course, moved into an ohter course, hidden or removed completely from the course room.</p>
<h2>Customize the Digisem plugin</h2>
<p>Administrators can edit the displayed configuration:</p>
![FTP config](/imgs/config-ftp.png "FTP config")
![Mail config](/imgs/config-mail.png "Mail config")
