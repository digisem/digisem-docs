Digisem Docs
============
<h2>What Is Digisem?</h2>

<p>
Digisem is a moodle plug-in that allows course owners to use their moodle courses as digital reserve shelves. (A digital reserve shelf is a collection of digitalized library book chapters, articles, ...)  Digisem integrates moodle with the library systems needed to digitalize and publish library items such as books and articles. 
</p>

<p><strong>Main features:</strong></p>
<ul>
 <li>Digisem provides an "easy to use" solution to attach digital copies of library items to a course room.</li>
 <li>Course owners can create "digisems" as moodle activities. </li>
 <li>The plug-in integrates moodle with the OPAC for literature retrieval. </li>
 <li>Orders are sent to the library using a SUBITO related email format for machine-to-machine communication. </li>
 <li>The digitalized copy of a book chapter or article is integrated into the course room automatically. </li>
 <li>All ordered files are stored in the moodle file system so that users can easily provide them in other course rooms as well. </li>
</ul>

<p>From ordering a specific item, publishing it in the moodle course and displaying it to the users, it involves quite a number of steps and thus challenges. The following story tries to sum up the most important steps and challenges:</p>

<h2>Why Did We Build It?</h2>
<ol>
<li>Bob teaches at the local university. He wants to set up a course room in moodle for his lecture on economics. He wants to provide the mandatory book chapters as digital copies in the course room. Also, he wants to assign them to the correct weeks so that his students know what to read. </li>
<li>Ideally, Bob thinks, after he ordered the copies and assigned them to the correct weeks or slots, he should not have anything further to do. This means, the library gets informed about his request and executes it. When the digital copy is ready, it should be automatically published in the course. </li>
<li>As long as the digital copy has not been published in the course room, Bob expects that he can see the request details and status, but his students cannot. They see the copy after it has arrived. </li>
<li>Alice from the library scans and publishes books as PDFs. She needs the library ID of each book to find it and the numbers of the pages to scan. Unfortunately, Bob does not know the library IDs of the books he owns himself. </li>
</ol>

<p>The digisem plugin tries to cover all these expectations. Read in the section about Process Design below on how it works in principle. The sections on the next pages describe how to <a href="https://github.com/digisem/digisem-docs/blob/master/Integration.md">integrate the plugin</a> and show <a href="https://github.com/digisem/digisem-docs/blob/master/Screenshots.md">screenshots</a>. </p>


<h2>How Is It Designed?</h2>

<h3>So how does digisem work?</h3>
<img src="imgs/digisem-process.png" width=800 align="top" />
<p>In the image above you see the three main processes. First, the course owner (or teacher) orders a digital copy from the library and the library processes the request. In the second step, the digisem plugin fetches the copy and publishes it in the course room. In the last step the students can open the copy such as they would view any other module (in moodle terms of speaking). </p>

<h3>How do I order a digital copy?</h3>
<img src="imgs/digisem-order.png" width=300 align="left" />
<p>First, the course owner orders a digital copy. Whether he starts in the moodle course or in the library catalogue does not make any difference. (Please refer to the <a href="https://github.com/digisem/digisem-docs/blob/master/Integration.md">Integration section</a> for more details!)</p>

<p>If he starts in the moodle course room, he justs adds another resource of the type Digisem. Thereafter he chooses a name and is then forwarded to the library catalogue. He selects the item in the catalogue which afterwards offers an option to go back to moodle. The course owner is then forwarded back to the moodle course room with the item information. (This is somehow magic at this point and we will come back to this later in the Integration section.)</p>

<p>Now he sees all the necessary information in the moodle dialog to add a new module. He provides the page numbers he is interested in and creates the digisem. The plugin now starts a request by sending an order email to the library system. The email contains all information about the desired item as well as a unique identifier for that request.</p>

<h3>How does the plugin publish the copy in the course room?</h3>
<img src="imgs/digisem-fetch.png" width=300 align="left" />
<!--
<p>As you will read in the Integration section below, there is a contract with the library system regarding the publication of digital copies. We decided to use email, FTP and a cronjob. </p>
<p>Then it works as follows: The library receives an email containing all the necessary information when the course owner created the digisem. A unique identifier for the digisem is included in the email. -->
<p>The library receives the order email and processes the order. When the item is scanned and the copy is ready, it is placed on a FTP share with the unique identifier as filename. </p>
<p>The moodle cron triggers a cronjob of the digisem plugin regularly. The cronjob reads all files from the FTP share and compares them to its open requests. If there is a match, the file is loaded from the FTP and integrated into the moodle file system. </p>

<h3>When do the students see the digital copy?</h3>
<img src="imgs/digisem-display.png" width=300 align="left" />
<p>Every Digisem module has a status. Either it is ordered (a request is pending) or delivered (a digital copy can be downloaded form the course room). When the copy was successfully loaded from the FTP of the library, the status is set to delivered. From this moment on, the students of the course can see the copy.</p>

<p>Also there are some additional "cherries": The digital copy is also available in the course owner's own files. This means that it can be freely inserted in other course rooms as well. Also, the course owner is informed via email when the digital copy has arrived. </p>

<h3>But what happens, if Alice from the library could not process the order successfully?</h3>
<p>Well... good question :). This is up to you as process designer. The digisem plugin ships the email address (and contact info) from the requesting course owner with the order email. But there is no automatic cancellation of digisems in case of an error yet. Maybe in the future? </p>
<p>NEXT: <a href="https://github.com/digisem/digisem-docs/blob/master/Integration.md">Integration or "what do I have to do to get the digisem plugin working"?</a></p>
