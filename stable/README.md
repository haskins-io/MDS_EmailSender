MDS_EmailSender
===============

MDS_EmailSender is a collection of PHP classes (in a single file) that allow 
easy sending of emails from within PHP. Currently it is a wrapper for the PHP 
mail function that aims to make creating and sending an email in PHP a bit more 
friendly.

It is very easy to use, just download the MDS_EmailSender.php file from this
folder, add it to your class, then create a message and send it.

<pre>
<?php

require_once ('MDS_EmailSender.php');

// First create a message<br/>
$emailMesage = new MDS_EmailSender_Message();<br/><br/>

// Say who it is from <br/>
$emailMesage->addFrom("Name <name@domain.com>");<br/><br/>

// Say who it is going to. You can call these multiple times if needed<br/>
$emailMesage->addToRecipient("Name <name@domain.com>");<br/>
$emailMesage->addCcRecipient("Name <name@domain.com>");  // Optional<br/>
$emailMesage->addBccRecipient("Name <name@domain.com>"); // Optional<br/><br/>

// Set the subject line<br/>
$emailMesage->setSubject("Test of the new Email Code");<br/><br/>

// Set the HTML and plain body. You can just either one if needed.<br/>
$emailMesage->setHtmlBody("<p>This is some HTML</p>");<br/>
$emailMesage->setPlainBody("This is some plain text");<br/><br/>

// Maybe add an attachment or two<br/>
$data = file_get_contents("/path/to/file/1.pdf");<br/>
$emailMesage->addAttachment($data, "application/pdf", "test.pdf");<br/><br/>


// Create a EmailSender<br/>
$emailSender = new MDS_EmailSender();<br/><br/>

// Send the email<br/>
$emailSender->send($emailMesage);<br/><br/>

?>
</pre>