
- [ ] Des noms prononçables  
Qu’est ce qui est plus facile à lire ?
<table>
<tr>
<td>
   <pre lang="csharp">
class DtaRcrd102{
    private DateTime genymdhms;
    private DateTime modymdhms;
    private String pszqint = "102";
/* ... */
};

   </pre>
</td>
<td>
  <pre lang="csharp">
class Customer{
    private DateTime generationTimestamp;
    private DateTime modificationTimestamp;;
    private String recordId = "102";
    /* ... */
};

  </pre>
</td>
</tr>
</table>
  
├── app
│   ├── css
│   │   ├── **/*.css
│   ├── favicon.ico
│   ├── images
│   ├── index.html
│   ├── js
│   │   ├── **/*.js
│   └── partials/template
├── dist (or build)
├── node_modules
├── bower_components (if using bower)
├── test
├── Gruntfile.js/gulpfile.js
├── README.md
├── package.json
├── bower.json (if using bower)
└── .gitignore
