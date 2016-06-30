---
layout: page
title: SQL Практическое занятие 1
permalink: /docs/practice/spec/sql/1/
---


Вас приняли на работу программистом на языке SQL в Acme Corporation. Ваше первое задание состоит в создании отчетов на основе данных из таблиц схемы Human Resources (“Персонал”, HR).


1\.	Ваше первое задание – выяснить структуру таблицы DEPARTMENTS и вывести ее содержимое.


    DESCRIBE departments;

<br/>

    Name            Null     Type         
    --------------- -------- ------------
    DEPARTMENT_ID   NOT NULL NUMBER(4)    
    DEPARTMENT_NAME NOT NULL VARCHAR2(30)
    MANAGER_ID               NUMBER(6)    
    LOCATION_ID              NUMBER(4)  


<br/>


Чтобы не было повторяющегося блока в заголовке, указываю, что на одной странице помещается 1024 записи. Цифра не имеет принципиального значения, но мне нравится 1024.

    SET PAGES 1024;

<br/>

    SELECT *
    FROM departments;

<br/>


    DEPARTMENT_ID DEPARTMENT_NAME                MANAGER_ID LOCATION_ID
    ------------- ------------------------------ ---------- -----------
               10 Administration                        200        1700
               20 Marketing                             201        1800
               30 Purchasing                            114        1700
               40 Human Resources                       203        2400
               50 Shipping                              121        1500
               60 IT                                    103        1400
               70 Public Relations                      204        2700
               80 Sales                                 145        2500
               90 Executive                             100        1700
              100 Finance                               108        1700
              110 Accounting                            205        1700
              120 Treasury                                         1700
              130 Corporate Tax                                    1700
              140 Control And Credit                               1700
              150 Shareholder Services                             1700
              160 Benefits                                         1700
              170 Manufacturing                                    1700
              180 Construction                                     1700
              190 Contracting                                      1700
              200 Operations                                       1700
              210 IT Support                                       1700
              220 NOC                                              1700
              230 IT Helpdesk                                      1700
              240 Government Sales                                 1700
              250 Retail Sales                                     1700
              260 Recruiting                                       1700
              270 Payroll                                          1700
                9 New                                   200        1700

     28 rows selected

<br/>


2\. Вам необходимо выяснить структуру таблицы EMPLOYEES

<br/>

    DESCRIBE employees;

<br/>

    Name           Null     Type         
    -------------- -------- ------------
    EMPLOYEE_ID    NOT NULL NUMBER(6)    
    FIRST_NAME              VARCHAR2(20)
    LAST_NAME      NOT NULL VARCHAR2(25)
    EMAIL          NOT NULL VARCHAR2(25)
    PHONE_NUMBER            VARCHAR2(20)
    HIRE_DATE      NOT NULL DATE         
    JOB_ID         NOT NULL VARCHAR2(10)
    SALARY                  NUMBER(8,2)  
    COMMISSION_PCT          NUMBER(2,2)  
    MANAGER_ID              NUMBER(6)    
    DEPARTMENT_ID           NUMBER(4)   


<br/>

    SELECT *
    FROM employees;

<br/>

3\. Отделу по работе с персоналом (Human Resources,  HR) необходимы данные, включающие фамилию, код должности, дату найма и табельный номер для каждого служащего. Табельный номер должен выводиться первым. Определите псевдоним STARTDATE для столбца HIRE_DATE.


    SELECT employee_id, last_name, job_id, hire_date as STARTDATE
    FROM employees;

<br/>

    EMPLOYEE_ID LAST_NAME                 JOB_ID     STARTDATE                     
    ----------- ------------------------- ---------- -------------------------------
            100 King                      AD_PRES    17-JUN-03                      
            101 Kochhar                   AD_VP      21-SEP-05                      
            102 De Haan                   AD_VP      13-JAN-01                      
            103 Hunold                    IT_PROG    03-JAN-06                      
            104 Ernst                     IT_PROG    21-MAY-07                      
            105 Austin                    IT_PROG    25-JUN-05                      
            106 Pataballa                 IT_PROG    05-FEB-06                      
            107 Lorentz                   IT_PROG    07-FEB-07                      
            108 Greenberg                 FI_MGR     17-AUG-02                      
            109 Faviet                    FI_ACCOUNT 16-AUG-02                      
            110 Chen                      FI_ACCOUNT 28-SEP-05                      
            111 Sciarra                   FI_ACCOUNT 30-SEP-05                      
            112 Urman                     FI_ACCOUNT 07-MAR-06                      
            113 Popp                      FI_ACCOUNT 07-DEC-07                      
            114 Raphaely                  PU_MAN     07-DEC-02                      
            115 Khoo                      PU_CLERK   18-MAY-03                      
            116 Baida                     PU_CLERK   24-DEC-05                      
            117 Tobias                    PU_CLERK   24-JUL-05                      
            118 Himuro                    PU_CLERK   15-NOV-06                      
            119 Colmenares                PU_CLERK   10-AUG-07                      
            120 Weissgbgg                 ST_MAN     18-JUL-04                      
            121 Fripp                     ST_MAN     10-APR-05                      
            122 Kaufling                  ST_MAN     01-MAY-03                      
            123 Vollman                   ST_MAN     10-OCT-05                      
            124 Mourgos                   ST_MAN     16-NOV-07                      
            125 Nayer                     ST_CLERK   16-JUL-05                      
            126 Mikkilineni               ST_CLERK   28-SEP-06                      
            127 Landry                    ST_CLERK   14-JAN-07                      
            128 Markle                    ST_CLERK   08-MAR-08                      
            129 Bissot                    ST_CLERK   20-AUG-05                      
            130 Atkinson                  ST_CLERK   30-OCT-05                      
            131 Marlow                    ST_CLERK   16-FEB-05                      
            132 Olson                     ST_CLERK   10-APR-07                      
            133 Mallin                    ST_CLERK   14-JUN-04                      
            134 Rogers                    ST_CLERK   26-AUG-06                      
            135 Gee                       ST_CLERK   12-DEC-07                      
            136 Philtanker                ST_CLERK   06-FEB-08                      
            137 Ladwig                    ST_CLERK   14-JUL-03                      
            138 Stiles                    ST_CLERK   26-OCT-05                      
            139 Seo                       ST_CLERK   12-FEB-06                      
            140 Patel                     ST_CLERK   06-APR-06                      
            141 Rajs                      ST_CLERK   17-OCT-03                      
            142 Davies                    ST_CLERK   29-JAN-05                      
            143 Matos                     ST_CLERK   15-MAR-06                      
            144 Vargas                    ST_CLERK   09-JUL-06                      
            145 Russell                   SA_MAN     01-OCT-04                      
            146 Partners                  SA_MAN     05-JAN-05                      
            147 Errazuriz                 SA_MAN     10-MAR-05                      
            148 Cambrault                 SA_MAN     15-OCT-07                      
            149 Zlotkey                   SA_MAN     29-JAN-08                      
            150 Tucker                    SA_REP     30-JAN-05                      
            151 Bernstein                 SA_REP     24-MAR-05                      
            152 Hall                      SA_REP     20-AUG-05                      
            153 Olsen                     SA_REP     30-MAR-06                      
            154 Cambrault                 SA_REP     09-DEC-06                      
            155 Tuvault                   SA_REP     23-NOV-07                      
            156 King                      SA_REP     30-JAN-04                      
            157 Sully                     SA_REP     04-MAR-04                      
            158 McEwen                    SA_REP     01-AUG-04                      
            159 Smith                     SA_REP     10-MAR-05                      
            160 Doran                     SA_REP     15-DEC-05                      
            161 Sewall                    SA_REP     03-NOV-06                      
            162 Vishney                   SA_REP     11-NOV-05                      
            163 Greene                    SA_REP     19-MAR-07                      
            164 Marvins                   SA_REP     24-JAN-08                      
            165 Lee                       SA_REP     23-FEB-08                      
            166 Ande                      SA_REP     24-MAR-08                      
            167 Banda                     SA_REP     21-APR-08                      
            168 Ozer                      SA_REP     11-MAR-05                      
            169 Bloom                     SA_REP     23-MAR-06                      
            170 Fox                       SA_REP     24-JAN-06                      
            171 Smith                     SA_REP     23-FEB-07                      
            172 Bates                     SA_REP     24-MAR-07                      
            173 Kumar                     SA_REP     21-APR-08                      
            174 Abel                      SA_REP     11-MAY-04                      
            175 Hutton                    SA_REP     19-MAR-05                      
            176 Taylor                    SA_REP     24-MAR-06                      
            177 Livingston                SA_REP     23-APR-06                      
            178 Grant                     SA_REP     24-MAY-07                      
            179 Johnson                   SA_REP     04-JAN-08                      
            180 Taylor                    SH_CLERK   24-JAN-06                      
            181 Fleaur                    SH_CLERK   23-FEB-06                      
            182 Sullivan                  SH_CLERK   21-JUN-07                      
            183 Geoni                     SH_CLERK   03-FEB-08                      
            184 Sarchand                  SH_CLERK   27-JAN-04                      
            185 Bull                      SH_CLERK   20-FEB-05                      
            186 Dellinger                 SH_CLERK   24-JUN-06                      
            187 Cabrio                    SH_CLERK   07-FEB-07                      
            188 Chung                     SH_CLERK   14-JUN-05                      
            189 Dilly                     SH_CLERK   13-AUG-05                      
            190 Gates                     SH_CLERK   11-JUL-06                      
            191 Perkins                   SH_CLERK   19-DEC-07                      
            192 Bell                      SH_CLERK   04-FEB-04                      
            193 Everett                   SH_CLERK   03-MAR-05                      
            194 McCain                    SH_CLERK   01-JUL-06                      
            195 Jones                     SH_CLERK   17-MAR-07                      
            196 Walsh                     SH_CLERK   24-APR-06                      
            197 Feeney                    SH_CLERK   23-MAY-06                      
            198 OConnell                  SH_CLERK   21-JUN-07                      
            199 Grant                     SH_CLERK   13-JAN-08                      
            200 Whalen                    PU_CLERK   17-SEP-03                      
            201 Hartstein                 MK_MAN     17-FEB-04                      
            202 Fay                       MK_REP     17-AUG-05                      
            203 Mavris                    HR_REP     07-JUN-02                      
            204 Baer                      PR_REP     07-JUN-02                      
            205 Higgins                   AC_MGR     07-JUN-02                      
            206 Gietz                     AC_ACCOUNT 07-JUN-02                      

     107 rows selected



4\. Отдел по работе с персоналом запрашивает данные о всех уникальных должностях из таблицы EMPLOYEES. В выводимых результатах идентификаторы должностей  не должны повторяться.


    SELECT distinct job_id
    FROM employees;

<br/>    

    JOB_ID   
    ----------
    AC_ACCOUNT
    AC_MGR    
    AD_PRES   
    AD_VP     
    FI_ACCOUNT
    FI_MGR    
    HR_REP    
    IT_PROG   
    MK_MAN    
    MK_REP    
    PR_REP    
    PU_CLERK  
    PU_MAN    
    SA_MAN    
    SA_REP    
    SH_CLERK  
    ST_CLERK  
    ST_MAN    

     18 rows selected


5\. Отделу HR необходим отчет о всех сотрудниках и идентификаторах их должностей. Выведите на экран имя сотрудника, соединенное с идентификатором должности через запятую и пробел.  Назовите новый столбец Employee and Title


    SELECT last_name || ', ' ||job_id as "Employee and Title"
    FROM employees;

<br/>

    Employee and Title                  
    -------------------------------------
    Abel, SA_REP                         
    Ande, SA_REP                         
    Atkinson, ST_CLERK                   
    Austin, IT_PROG                      
    Baer, PR_REP                         
    Baida, PU_CLERK                      
    Banda, SA_REP                        
    Bates, SA_REP                        
    Bell, SH_CLERK                       
    Bernstein, SA_REP                    
    Bissot, ST_CLERK                     
    Bloom, SA_REP                        
    Bull, SH_CLERK                       
    Cabrio, SH_CLERK                     
    Cambrault, SA_MAN                    
    Cambrault, SA_REP                    
    Chen, FI_ACCOUNT                     
    Chung, SH_CLERK                      
    Colmenares, PU_CLERK                 
    Davies, ST_CLERK                     
    De Haan, AD_VP                       
    Dellinger, SH_CLERK                  
    Dilly, SH_CLERK                      
    Doran, SA_REP                        
    Ernst, IT_PROG                       
    Errazuriz, SA_MAN                    
    Everett, SH_CLERK                    
    Faviet, FI_ACCOUNT                   
    Fay, MK_REP                          
    Feeney, SH_CLERK                     
    Fleaur, SH_CLERK                     
    Fox, SA_REP                          
    Fripp, ST_MAN                        
    Gates, SH_CLERK                      
    Gee, ST_CLERK                        
    Geoni, SH_CLERK                      
    Gietz, AC_ACCOUNT                    
    Grant, SH_CLERK                      
    Grant, SA_REP                        
    Greenberg, FI_MGR                    
    Greene, SA_REP                       
    Hall, SA_REP                         
    Hartstein, MK_MAN                    
    Higgins, AC_MGR                      
    Himuro, PU_CLERK                     
    Hunold, IT_PROG                      
    Hutton, SA_REP                       
    Johnson, SA_REP                      
    Jones, SH_CLERK                      
    Kaufling, ST_MAN                     
    Khoo, PU_CLERK                       
    King, SA_REP                         
    King, AD_PRES                        
    Kochhar, AD_VP                       
    Kumar, SA_REP                        
    Ladwig, ST_CLERK                     
    Landry, ST_CLERK                     
    Lee, SA_REP                          
    Livingston, SA_REP                   
    Lorentz, IT_PROG                     
    Mallin, ST_CLERK                     
    Markle, ST_CLERK                     
    Marlow, ST_CLERK                     
    Marvins, SA_REP                      
    Matos, ST_CLERK                      
    Mavris, HR_REP                       
    McCain, SH_CLERK                     
    McEwen, SA_REP                       
    Mikkilineni, ST_CLERK                
    Mourgos, ST_MAN                      
    Nayer, ST_CLERK                      
    OConnell, SH_CLERK                   
    Olsen, SA_REP                        
    Olson, ST_CLERK                      
    Ozer, SA_REP                         
    Partners, SA_MAN                     
    Pataballa, IT_PROG                   
    Patel, ST_CLERK                      
    Perkins, SH_CLERK                    
    Philtanker, ST_CLERK                 
    Popp, FI_ACCOUNT                     
    Rajs, ST_CLERK                       
    Raphaely, PU_MAN                     
    Rogers, ST_CLERK                     
    Russell, SA_MAN                      
    Sarchand, SH_CLERK                   
    Sciarra, FI_ACCOUNT                  
    Seo, ST_CLERK                        
    Sewall, SA_REP                       
    Smith, SA_REP                        
    Smith, SA_REP                        
    Stiles, ST_CLERK                     
    Sullivan, SH_CLERK                   
    Sully, SA_REP                        
    Taylor, SA_REP                       
    Taylor, SH_CLERK                     
    Tobias, PU_CLERK                     
    Tucker, SA_REP                       
    Tuvault, SA_REP                      
    Urman, FI_ACCOUNT                    
    Vargas, ST_CLERK                     
    Vishney, SA_REP                      
    Vollman, ST_MAN                      
    Walsh, SH_CLERK                      
    Weissgbgg, ST_MAN                    
    Whalen, PU_CLERK                     
    Zlotkey, SA_MAN                      

     107 rows selected
