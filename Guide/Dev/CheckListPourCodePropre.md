
- [ ] **Des noms prononçables**  
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
  +-------+----------+------+
| Table Headings   | Here |
+-------+----------+------+
| Sub   | Headings | Too  |
+=======+==========+======+
| cell  | column spanning |
+ spans +----------+------+
| rows  | normal   | cell |
+-------+----------+------+
| multi | * cells can be  |
| line  | * formatted     |
| cells | * paragraphs    |
| too   |                 |
+-------+-----------------+
