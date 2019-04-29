# Flysystem Adapter for the FTP with cURL implementation

This package contains a [Flysystem](https://flysystem.thephpleague.com/) FTP adapter with cURL implementation.
It supports both explicit and implicit SSL connections.

## Installation

You can install the package via composer:

``` bash
composer require chinlung/flysystem-curlftp
```

## Usage

``` php
use League\Flysystem\Filesystem;
use ChinLung\Flysystem\CurlFtpAdapter;

$adapter = new CurlFtpAdapter([
  'host' => 'ftp.example.com',
  'username' => 'username',
  'password' => 'password',

  /** optional config settings */
  'port' => 21,
  'root' => '/path/to/root',
  'utf8' => true,
  'ftps' => true, // use ftps:// with implicit TLS or ftp:// with explicit TLS
  'ssl' => true,
  'timeout' => 90, // connect timeout
  'passive' => true, // default use PASV mode
  'skipPasvIp' => true, // ignore the IP address in the PASV response 
  'sslVerifyPeer' => 0, // using 0 is insecure, use it only if you know what you're doing
  'sslVerifyHost' => 0, // using 0 is insecure, use it only if you know what you're doing
  
  /** proxy settings */
  'proxyHost' => 'proxy-server.example.com',
  'proxyPort' => 80,
  'proxyUsername' => 'proxyuser',
  'proxyPassword' => 'proxypassword',
  
  'verbose' => false // set verbose mode on/off 
]);

$filesystem = new Filesystem($adapter);
``` 

## Testing

``` bash
$ composer test
```

## Security

If you discover any security related issues, please email chinlung.shih@gmail.com instead of using the issue tracker.

## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.
