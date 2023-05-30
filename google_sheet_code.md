# Google sheet code

Author: Huanfa Chen

Last update: 2023/05/30

1. To exclude a value in Cell A3 from a list 

   ```basic
   =filter({"aa","bb","cc","dd","ee"},{"aa","bb","cc","dd","ee"}<>A3)
   ```

   

2. To randomly pick up a value from a list that excludes a value in A3. Note that the random selection depends on all cells in this speadsheet, meaning that if you change any cell in the spreadsheet, the random value will change.

   ```basic
   =INDEX(filter({"aa","bb","cc","dd","ee"},{"aa","bb","cc","dd","ee"}<>A3)), RANDBETWEEN(1,COUNTA({"aa","bb","cc","dd","ee"})-1)))
   ```

3. To do something conditioning on whether a cell A3 is blank

   ```basic
   =if(isblank(A3), sth, sth_else)
   ```

   

4. 