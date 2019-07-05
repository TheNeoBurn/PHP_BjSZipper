# PHP_BjSZipper
A PHP class to stream files as an uncompressed ZIP archive without a temporary file

Detailed information is on CodeProject:

<a href="https://www.codeproject.com/Articles/3839889/Streaming-ZIP-File-in-PHP-Without-Temp-File">[3839889] Streaming ZIP File in PHP Without Temp File</a>

<h2>General code usage</h2>

<h3>Collecting information and sending with progress bar working</h3>

<pre>
require_once('BjSZipper.php');

// Create a new instance
$zip = new BjSZipper('images.zip');

// Add files and data to send
$zip->AddDir(dirname(__FILE__), true, '/\.(jpg|jpeg)/i'); // All JPEGs recursively
$zip->AddFile('/var/www/html/testdata.bin');              // Just a normal file
$zip->AddData('All the JPEG images.', 'desc.txt');        // A raw text file

// Start sending the archive
$zip->Send();
</pre>

<h3>Sending immediately but without working progress bar</h3>

<pre>
require_once('BjSZipper.php');

// Send the HTTP headers
BjSZipper::Begin('images.zip');

// Add files and data to send
BjSZipper::SendDir(dirname(__FILE__), true, '/\.(jpg|jpeg)/i'); // All JPEGs recursively
BjSZipper::SendFile('/var/www/html/testdata.bin');              // Just a normal file
BjSZipper::SendData('All the JPEG images.', 'desc.txt');        // A raw text file

// Send the archive directory and end the archive
BjSZipper::End();
</pre>
