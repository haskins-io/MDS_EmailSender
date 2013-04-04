MDS_EmailSender
===============

MDS_EmailSender is a collection of PHP classes (in a single file) that allow 
easy sending of emails from within PHP. Currently it is a wrapper for the PHP 
mail function that aims to make creating and sending an email in PHP a bit more 
friendly.

It is very easy to use, just download the MDS_EmailSender.php file from this
folder, add it to your class, then create a message and send it.

<?php

require_once ('MDS_EmailSender.php');

// First create a message
$emailMesage = new MDS_EmailSender_Message();

// Say who it is from 
$emailMesage->addFrom("Name <name@domain.com>");

// Say who it is going to. You can call these multiple times if needed
$emailMesage->addToRecipient("Name <name@domain.com>");
$emailMesage->addCcRecipient("Name <name@domain.com>");  // Optional
$emailMesage->addBccRecipient("Name <name@domain.com>"); // Optional

// Set the subject line
$emailMesage->setSubject("Test of the new Email Code");

// Set the HTML and plain body. You can just either one if needed.
$emailMesage->setHtmlBody("<p>This is some HTML</p>");
$emailMesage->setPlainBody("This is some plain text");

// Maybe add an attachment or two
$data = file_get_contents("/path/to/file/1.pdf");
$emailMesage->addAttachment($data, "application/pdf", "test.pdf");


// Create a EmailSender
$emailSender = new MDS_EmailSender();

// Send the email
$emailSender->send($emailMesage);

?>