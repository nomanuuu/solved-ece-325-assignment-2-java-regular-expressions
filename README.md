Download Link: https://assignmentchef.com/product/solved-ece-325-assignment-2-java-regular-expressions
<br>
Java Regular Expressions

Valid or invalid that is the question?

Web applications have several challenges; perhaps the most serious being the difficultly in maintaining state information. A common solution to this issue is to use cookies as a mechanism to encode and distribute this information. However, as the cookie passes from a server to a client and back neither side can assume that the cookie is valid.

You are required to produce a Java program, which uses the regular expression to answer the question: “Is this cookie (supplied as an input) valid or not?”

For this assignment, a valid cookie is defined by these subset of rules found in RFC 6265 (HTTP State Management Mechanism), along with RFC 2616, RFC 1123, and RFC 1034. Note that only the rules in this assignment have to be implemented. A fully functional cookie checker is not required.

<table width="575">

 <tbody>

  <tr>

   <td width="575">set-cookie-header = “Set-Cookie:” SP set-cookie-string set-cookie-string = cookie-pair *( “;” SP cookie-av ) cookie-pair       = cookie-name “=” cookie-value cookie-name       = tokentoken             = 1*&lt;any CHAR except CTLs or separators&gt;separators        = “(” | “)” | “&lt;” | “&gt;” | “@”| “,” | “;” | “:” | “” | &lt;“&gt;| “/” | “[” | “]” | “?” | “=”| “{” | “}” | SP | HTcookie-value      = *cookie-octet / ( DQUOTE *cookie-octet DQUOTE )cookie-octet      = %x21 / %x23-2B / %x2D-3A / %x3C-5B / %x5D-7E; US-ASCII characters excluding CTLs,; whitespace DQUOTE, comma, semicolon,; and backslashcookie-av         = expires-av / max-age-av / domain-av /path-av / secure-av / httponly-av expires-av        = “Expires=” rfc1123-daterfc1123-date      = wkday “,” SP date1 SP time SP “GMT” date1             = 2DIGIT SP month SP 4DIGIT; day month year (e.g., 02 Jun 1982) time              = 2DIGIT “:” 2DIGIT “:” 2DIGIT; 00:00:00 – 23:59:59 wkday             = “Mon” | “Tue” | “Wed”                   | “Thu” | “Fri” | “Sat” | “Sun” month             = “Jan” | “Feb” | “Mar” | “Apr”| “May” | “Jun” | “Jul” | “Aug”| “Sep” | “Oct” | “Nov” | “Dec”max-age-av        = “Max-Age=” non-zero-digit *DIGIT non-zero-digit    = %x31-39; digits 1 through 9domain-av         = “Domain=” domain-value domain-value      = &lt;domain&gt; path-av           = “Path=” path-valuepath-value        = &lt;any CHAR except CTLs or “;”&gt; secure-av         = “Secure” httponly-av       = “HttpOnly”&lt;domain&gt;        ::= &lt;subdomain&gt; | ” ”&lt;subdomain&gt;     ::= &lt;label&gt; | &lt;subdomain&gt; “.” &lt;label&gt;&lt;label&gt;         ::= &lt;letter&gt; [ [ &lt;ldh-str&gt; ] &lt;let-dig&gt; ]&lt;ldh-str&gt;       ::= &lt;let-dig-hyp&gt; | &lt;let-dig-hyp&gt; &lt;ldh-str&gt;&lt;let-dig-hyp&gt;   ::= &lt;let-dig&gt; | “-”&lt;let-dig&gt;       ::= &lt;letter&gt; | &lt;digit&gt;&lt;letter&gt;        ::= any one of the 52 alphabetic characters A through Z in upper case and a through &lt;digit&gt;         ::= any one of the ten digits 0 through 9</td>

  </tr>

 </tbody>

</table>

z

<table width="573">

 <tbody>

  <tr>

   <td width="573">Hint: to understand the definition, you may need Augmented Backus-Naur Form.Examples/TestcasesHere are the examples of cookies (test cases, both valid and invalid) to assist you in cons</td>

  </tr>

  <tr>

   <td width="573">HTTP/1.x 200 OKServer: Apache-Coyote/1.11.                   Set-Cookie: ns1=”alss/0.foobar^”                        # name=value2.                   Set-Cookie: ns1=                                        # empty value3.                   Set-Cookie: ns1=; Expires=Wed, 19 Nov 2008 16:35:39 GMT  # Expires=time_stamp4.                   Set-Cookie: ns1=; Domain=                                # empty Domain5.                   Set-Cookie: ns1=; Domain=.srv.a.com-0                    # Domain=host_name6.                   Set-Cookie: lu=Rg3v; Expires=Wed, 19 Nov 2008 16:35:39 GMT; Path=/; Domain=.example.com; HttpOnly7.                   Set-Cookie:                                             # empty cookie-pair8.                   Set-Cookie: sd                                          # no “=”9.                   Set-Cookie: =alss/0.foobar^                             # empty name10.                 Set-Cookie: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="3b55487b0a">[email protected]</a>=alss/0.foobar^                         # illegal name11.                 Set-Cookie: ns1=alss/0.foobar^;                         # trailing “;”12.                 Set-Cookie: ns1=; Expires=Wed 19 Nov 2008 16:35:39 GMT   # illegal Expires value13.                 Set-Cookie: ns1=alss/0.foobar^; Max-Age=01              # illegal Max-Age: starting 014.                 Set-Cookie: ns1=alss/0.foobar^; Domain=.0com            # illegal Domain: starting 015.                 Set-Cookie: ns1=alss/0.foobar^; Domain=.com-            # trailing non-letter-digit Domain16.                 Set-Cookie: ns1=alss/0.foobar^; Path=                   # empty Path17.                 Set-Cookie: ns1=alss/0.foobar^; httponly                # lower case of “HttpOnly” Cache-Control: privatePragma: no-cacheContent-Encoding: gzipContent-Type: text/html;charset=UTF-8Content-Length: 22784Date: Tue, 18 Nov 2008 16:35:39 GMT</td>

  </tr>

 </tbody>

</table>