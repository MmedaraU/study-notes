- [References](#references)
- [How the Web Works](#how-the-web-works)
  - [The Internet vs The Web](#the-internet-vs-the-web)
  - [Serving up Information](#serving-up-information)
  - [About Browsers](#about-browsers)
  - [Intranets and Extranets](#intranets-and-extranets)
  - [Web Page Addresses (URLs)](#web-page-addresses-urls)
  - [Parts of a URL](#parts-of-a-url)
- [Some Concepts to Know](#some-concepts-to-know)

# References
> Learning Web Design: A Beginner's Guide to HTML, CSS, JavaScript and Web Graphics, *4th Edition* by Jennifer Niederst Robbins

# How the Web Works

## The Internet vs The Web
The *Internet* is a network of connected computers, owned by no one. It is a cooperative effort governed by a system of standards and rules.  
The purpose of connecting computers is to share information. There are many ways to share information between computers - email, file transfer (FTP), etc.
These standardized methods for transferring data or documents over a network are known as *protocols*.

The *Web* (also known as the World Wide Web) is just one of the ways information can be shared over the Internet. The Web is a subset of the Internet.  
Allows documents to be linked to one another using hypertext links, thus forming a huge 'web' of connected information.  
The Web uses a protocol called *HTTP* (HyperText Transfer Protocol). 

## Serving up Information

*Servers* are computer that serve up documents upon request. More accurately, it is the software that allows the computer to communicate with other computers.

For a computer to be a server, it must be running special server software that allows it handle HTTP transactions.

Web Servers are also called HTTP servers. Every computer and device connected to the INternet is assigned a unique numeric IP address. However, the Domain Name System (DNS) was developed to allow us refer to that server by its domain name ("oreilly.com"). Matching the domain name to the IP address is the job of a separate DNS server.

It is possible to configure your web server so more than one domain name is mapped to a single IP address.

The *IANA* is the organisation that assigns IP numbers.

## About Browsers
The *client* is the software that does the requesting. Browsers and other assistive technologies are used as clients to access documents on the Web.

The requests and responses are handled via the HTTP protocol. 

## Intranets and Extranets
*Intranets* are special web-based networks which allow for sharing of information just within a select few (e.g an organisation).

*Extranets* are like intranets, only access to select users outside the organisation.

## Web Page Addresses (URLs)
*URL* stands for Uniform Resource Locator. 

## Parts of a URL

`http://www.example.com/2011/samples/first.html`

* `http://` - The protocol that will be used for the particular transaction.

* `www.example.com` - The domain name of the website.
  * `www` - host name

* `/2012/samples/first.html` - The absolute path through directories on the server to the requested HTML document.


# Some Concepts to Know

1. Progressive enhancement: Designing a baseline experience that makes content availble to even the most rudimentary browsers, and later adding more advanced features for browsers that can handle them.

2. Graceful degradation: This is the flip side of progressive enhancement. It starts by building the decked-ot version of the site and later including support for older or non-supporting browsers.

3. Responsive Web Design: A strategy for providing custom layouts to devices based on their viewport sizes.













