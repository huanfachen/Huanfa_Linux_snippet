# Google sheet code

Author: Huanfa Chen

Last update: 2023/05/30

The Google sheet used for code demonstration: [here](https://docs.google.com/spreadsheets/d/1oniOL0mffvB3OTnuo8rBeRgQR7cxhb5POHdLZYfPj-A/edit?usp=sharing)

1. To exclude a value in Cell A3 from a list 

   ```basic
   =filter({"aa","bb","cc","dd","ee"},{"aa","bb","cc","dd","ee"}<>A3)
   ```

2. To randomly pick up a value from a list that excludes a value in A3. Note that the random selection depends on all cells in this speadsheet, meaning that if you change any cell in the spreadsheet, the random value will change.

   ```basic
   =INDEX(filter({"aa","bb","cc","dd","ee"},{"aa","bb","cc","dd","ee"}<>A3)), RANDBETWEEN(1,COUNTA({"aa","bb","cc","dd","ee"})-1)))
   ```

3. To do something conditioning on whether a cell A3 is blank

   ```visual basic
   =if(isblank(A3), sth, sth_else)
   ```

4. To count the number of cells in a range (Column A) that equals to a value ("")

   ```
   =count(A:A,"")
   ```

5. To count the number of cells that meets a criterion (greater than 5)

   ```visual basic
   =countif(A:A,">5")
   ```

6. To count the number of cells that meets multiple criteria from multiple columns. Note that countifs doesn't work with isnumber or isna

   ```
   =countifs(A:A,">5",B:B,"")
   ```

7. To group by a column and get the sum of the values in another column (using SQL syntax)

   ```
   =QUERY(A2:C8,"select A, sum(D) group by A")
   ```

   

 

