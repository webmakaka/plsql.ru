---
layout: page
title: Преобразование значений NULL в не-NULL значения (COALESCE)
description: Преобразование значений NULL в не-NULL значения (COALESCE)
keywords: Преобразование значений NULL в не-NULL значения (COALESCE)
permalink: /books/molinaro/retrieving_records/transforming-nulls-into-real-values/
---

# Преобразование значений NULL в не-NULL значения (COALESCE)

### Задача

Имеются строки, содержащие NULL значения, и требуется возвратить не-NULL значения вместо имеющихся NULL.

<h3>Решение</h3>

Чтобы подставить не-NULL занчепние вместо NULL, используйте функцию COALESCE:

    select coalesce(e.comm,0)
    from emp e

<br/>

    COALESCE(E.COMM,0)
    ------------------
                     0
                   300
                   500
                     0
                  1400
                     0
                     0
                     0
                     0
                     0
                     0
                     0
                     0
                     0

     14 rows selected

<br/>
<h3>Обсуждение</h3>

Функия COALESCE принимает в качестве аргументов одно или более значений. Функция возвращает первое не-NULL значение из списка. В данном решении. если значение COMM NULL, то возвращается ноль. В противном случае возвращается значение COMM.
