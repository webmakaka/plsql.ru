---
layout: page
title: Даты
permalink: /sql/dates/
---

    //        1 - Текущий день
    //        2 - Вчера
    //        3 - Эта неделя -
    //        4 - Текущий месяц
    //        5 - Текущий квартал



    case "1":  WhereClauseParams = "TRUNC(DATE_CREATION) = TRUNC(SYSDATE)";
             break;
    case "2":  WhereClauseParams = "TRUNC(DATE_CREATION) = TRUNC(SYSDATE-1)";
             break;
    case "3":  WhereClauseParams = "TRUNC(DATE_CREATION) BETWEEN ((sysdate, 'IW')-1) AND TRUNC(SYSDATE)";
             break;
    case "4":  WhereClauseParams = "TO_CHAR(DATE_CREATION,'fmMONTH') = TO_CHAR(sysdate,'fmMONTH')";
             break;
    case "5":  WhereClauseParams = "TRUNC(DATE_CREATION) BETWEEN TRUNC(SYSDATE-120) AND TRUNC(SYSDATE)";
             break;
