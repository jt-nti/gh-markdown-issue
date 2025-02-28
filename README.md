# gh-markdown-issue

Investigate problem with GitHub markdown related css.

It looks like there's a padding issue with html tables containing preformatted text in GitHub README.md files. There seems to be a [related pull request](https://github.com/primer/css/pull/2365) which added a fix for other elements, however the `margin-bottom: 0` added in that PR is getting overriden somewhere.

For example...

```
<table>
  <tr>
    <th>Tool</th>
    <th>Command</th>
  </tr>
  <tr>
    <td>Maven Wrapper (Linux/Mac)</td>
    <td><pre lang="shell">./mvnw clean verify</pre></td>
  </tr>
  <tr>
    <td>Maven Wrapper (Windows)</td>
    <td><pre lang="shell">mvnw.cmd clean verify</pre></td>
  </tr>
  <tr>
    <td>Maven (command-line)</td>
    <td><pre lang="shell">mvn clean verify</pre></td>
  </tr>
</table>
```

Should look like this (strangely, the formatting is correct when using the preview but has the unwanted bottom margin when viewing existing files):

<img width="478" alt="image" src="https://github.com/user-attachments/assets/97cfc012-3709-451a-81cf-c9416e5b6871" />

But currently looks like this:

<table>
  <tr>
    <th>Tool</th>
    <th>Command</th>
  </tr>
  <tr>
    <td>Maven Wrapper (Linux/Mac)</td>
    <td><pre lang="shell">./mvnw clean verify</pre></td>
  </tr>
  <tr>
    <td>Maven Wrapper (Windows)</td>
    <td><pre lang="shell">mvnw.cmd clean verify</pre></td>
  </tr>
  <tr>
    <td>Maven (command-line)</td>
    <td><pre lang="shell">mvn clean verify</pre></td>
  </tr>
</table>
