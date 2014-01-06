Integrating the Digisem Plugin
============

<p>
The Digisem plugin allows to order and publish digital copies from library items such as books, articles and so on. It is needless to say that, if you want to use the plugin, you need to integrate the plugin with certain library systems. The Digisem plugin uses the following interfaces:
</p>

<p><strong>Interfaces</strong></p>
<ol>
<li><p>The <underline>Library Catalogue Interface</underline> is needed to transfer the meta information of the library items such as books to the Digisem plugin. This is useful later in the library publishing system to look up which item must be scanned and where it is located. The library catalogue usually provides the possibility to send meta information to external systems. Most commonly this is done by using a HTTP request and passing the meta information via HTTP request parameters. </p>
<p>The Library Catalogue Interface provides specific HTTP GET parameters for e.g. the library ID, book name, author and year of publication.</p> </li>
<li>The <underline>Library Publishing Interface</underline></p> is used to transmit the meta information of the library item (e.g. book) and the order information to the library. In the next step the item is then located, scanned and published. The Digisem plugin sends an email with a SUBITO related format. </li>
<li><p><underline>FTP Transfer Interface</underline>: Moodle has a cron function (/admin/cron.php). The cronjob must be triggered regularly, for instance all five minutes. The Digisem plugin cronjob is called by the moodle cron. It reads all file names from a given FTP (FTP/SFTP/FTPs) directory and compares them to the open digisem orders. </p>
<p>The library publishing system must thus be configured to place the scanned items into the FTP directory. Also the library publishing system must assert that the filenames match the digisem IDs (provided in each order email). 
</p></li>
</ol>
