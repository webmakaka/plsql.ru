---
layout: page
title: Сумма Прописью PLSQL
description: Сумма Прописью PLSQL
keywords: PLSQL, Сумма Прописью
permalink: /other/summa_propis/
---

# Сумма Прописью PLSQL

<br/>

    CREATE OR REPLACE FUNCTION get_sum_str (source IN NUMBER)
    RETURN varchar2 is result VARCHAR2(300);
    BEGIN
    -- k - копейки
      if source < 1
         then
            result := 'ноль '||
               ltrim(
                     to_char(
                             source,'9,9,,9,,,,,,9,9,,9,,,,,9,9,,9,,,,9,9,,9,,,.99'
                            )
                    ) || 'k';
         else
            result := ltrim(
                            to_char
                            (
                             source,'9,9,,9,,,,,,9,9,,9,,,,,9,9,,9,,,,9,9,,9,,,.99'
                            )
                           ) || 'k';
      end if;

    -- t - тысячи; m - милионы; M - миллиарды;
      result := replace( result, ',,,,,,', 'eM');
      result := replace( result, ',,,,,', 'em');
      result := replace( result, ',,,,', 'et');
    -- e - единицы; d - десятки; c - сотни;
      result := replace( result, ',,,', 'e');
      result := replace( result, ',,', 'd');
      result := replace( result, ',', 'c');
    -- Удаление незначащих нулей
      result := replace( result, '0c0d0et', '');
      result := replace( result, '0c0d0em', '');
      result := replace( result, '0c0d0eM', '');

    -- Обработка сотен
      result := replace( result, '0c', '');
      result := replace( result, '1c', 'сто ');
      result := replace( result, '2c', 'двести ');
      result := replace( result, '3c', 'триста ');
      result := replace( result, '4c', 'четыреста ');
      result := replace( result, '5c', 'пятьсот ');
      result := replace( result, '6c', 'шестьсот ');
      result := replace( result, '7c', 'семьсот ');
      result := replace( result, '8c', 'восемьсот ');
      result := replace( result, '9c', 'девятьсот ');

    -- Обработка десятков
      result := replace( result, '1d0e', 'десять ');
      result := replace( result, '1d1e', 'одиннадцать ');
      result := replace( result, '1d2e', 'двенадцать ');
      result := replace( result, '1d3e', 'тринадцать ');
      result := replace( result, '1d4e', 'четырнадцать ');
      result := replace( result, '1d5e', 'пятнадцать ');
      result := replace( result, '1d6e', 'шестнадцать ');
      result := replace( result, '1d7e', 'семнадцать ');
      result := replace( result, '1d8e', 'восемнадцать ');
      result := replace( result, '1d9e', 'девятнадцать ');
      result := replace( result, '0d', '');
      result := replace( result, '2d', 'двадцать ');
      result := replace( result, '3d', 'тридцать ');
      result := replace( result, '4d', 'сорок ');
      result := replace( result, '5d', 'пятьдесят ');
      result := replace( result, '6d', 'шестьдесят ');
      result := replace( result, '7d', 'семьдесят ');
      result := replace( result, '8d', 'восемьдесят ');
      result := replace( result, '9d', 'девяносто ');

    -- Обработка единиц
      result := replace( result, '0e', '');
      result := replace( result, '5e', 'пять ');
      result := replace( result, '6e', 'шесть ');
      result := replace( result, '7e', 'семь ');
      result := replace( result, '8e', 'восемь ');
      result := replace( result, '9e', 'девять ');
    --
      result := replace( result, '1e.', 'один рубль ');
      result := replace( result, '2e.', 'два рубля ');
      result := replace( result, '3e.', 'три рубля ');
      result := replace( result, '4e.', 'четыре рубля ');
      result := replace( result, '1et', 'одна тысяча ');
      result := replace( result, '2et', 'две тысячи ');
      result := replace( result, '3et', 'три тысячи ');
      result := replace( result, '4et', 'четыре тысячи ');
      result := replace( result, '1em', 'один миллион ');
      result := replace( result, '2em', 'два миллиона ');
      result := replace( result, '3em', 'три миллиона ');
      result := replace( result, '4em', 'четыре миллиона ');
      result := replace( result, '1eM', 'один миллиард ');
      result := replace( result, '2eM', 'два миллиарда ');
      result := replace( result, '3eM', 'три миллиарда ');
      result := replace( result, '4eM', 'четыре миллиарда ');

    -- Обработка копеек
      result := replace( result, '11k', '11 копеек');
      result := replace( result, '12k', '12 копеек');
      result := replace( result, '13k', '13 копеек');
      result := replace( result, '14k', '14 копеек');
      result := replace( result, '1k', '1 копейка');
      result := replace( result, '2k', '2 копейки');
      result := replace( result, '3k', '3 копейки');
      result := replace( result, '4k', '4 копейки');

    -- Обработка названий групп
      result := replace( result, '.', 'рублей ');
      result := replace( result, 't', 'тысяч ');
      result := replace( result, 'm', 'миллионов ');
      result := replace( result, 'M', 'милиардов ');
      result := replace( result, 'k', ' копеек');
    --
      RETURN(result);
    END get_sum_str;

<br/>

    select get_sum_str(123.88) from dual;
