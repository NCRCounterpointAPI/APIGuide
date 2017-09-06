# Troubleshooting TLS Issues

The NCR Counterpoint API installs a self-signed certificate that is valid with TLS 1.2, but based on server configurations, you may see issues where it wants to use TLS 1.1, older ciphers, or not work at all.  Here are some troubleshooting tips if you want to continue with this certificate instead of purchasing one from a 3rd party certificate authority.

* Firefox - throws an error saying Self-Signed certificates are not safe/supported.
  * Add exceptions to Firefox to allow this manually.  If you can allow just the 1 site that would be best.
* Windows 10
  * The setup delivered by the install works with TLS 1.2 and Chrome.
* Windows 7 - Windows 7 throws error messages on different browsers based on the server configuration around TLS and the ciphers available.
  * With TLS 1.1 and 1.2 on, the cipher/TLS version used may show as 1.1 and throw a warning in the security log about an obsolete cipher.  However, Chrome still shows this as valid and secure (the lock icon in the address bar, no warning about being unsafe).  If you plan to leave TLS 1.1 on, it should be safe to ignore the warning.  If you need it to say TLS 1.2, try the steps in the next bullet point.
  * With TLS 1.1 off (only TLS 1.2 on), the page may not load at all because it can't use the correct ciphers.
    * Make sure Chrome is updated.  Chrome has it's own list of ciphers that are independent of Windows when it comes to order and usage.
    * We recommend moving the cipher TLS_RSA_WITH_AES_128_GCM_SHA256 to the top of the list in Windows.  You can use a program like IIS Crypto to do this or try editing group policy / network / SSL settings.
      * Alternatively, it looks like Microsoft has issued a patch to set the cipher orders for 1.2 (https://technet.microsoft.com/library/security/3042058.aspx).  You can try this, but we have not validated that is a fix on it's own.
