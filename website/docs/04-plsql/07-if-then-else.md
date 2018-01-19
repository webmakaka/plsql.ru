---
layout: page
title: Условная логика (IF, IF-THEN-ELSE, IF-THEN-ELSIF-THEN-ELSE)
permalink: /plsql/if-then-else/
---

### Условная логика (IF, IF-THEN-ELSE, IF-THEN-ELSIF-THEN-ELSE)



В PL/SQL для выполнения условий логики можно использовать ключевые слова IF, THEN, ELSE, ESEIF и END IF


### Прототип IF


    IF [NOT] left_operand1 = right_operand1 [[AND|OR]
       [NOT] left_operand2 = right_operand2 [[AND|OR]
       [NOT] boolean_operand ]] THEN
      NULL;
    ELSE
      NULL;
    END IF;



### Прототип If-then-else

    IF [NOT] {comparison_expression | boolean_value} [[AND | OR]
             {comparison_expression | boolean_value}] THEN
      true_execution_block;
    [ELSE
        false_execution_block;]
    END IF;


### Прототип If-then-elsif-then-else


     IF    [NOT] {comparison_expression | boolean_value} [[AND | OR]
                 {comparison_expression | boolean_value}] THEN
      true_if_execution_block;
    [ELSIF [NOT] {comparison_expression | boolean_value} [[AND | OR]
                 {comparison_expression | boolean_value}] THEN
      true_elsif_execution_block;
    [ELSE
      all_false_execution_block;]
     END IF;


<strong>Пример:</strong>

    IF условаие1 THEN
    операторы1
    ELSEIF условие2 THEN
    операторы2
    ELSE
    операторы3
    END IF;


<ul>
<li>условие 1 и условие 2 являются булевыми (логическими выражениями, принимающими значения true (истина) и false (ложь)</li>
<li>операторы1, операторы2 и операторы3 являются операторами PL/SQL</li>
</ul>

<br/>

Эта условная логика выполняется следующим образом:

<ul>
<li>Если условие 1 истинно, выполняются операторы1</li>
<li>Если условие 1 ложно, но условие2 истинно, выполняются операторы2</li>
<li>Если ни условие 1, ни условие2 не являются истинными, выполняются операторы3</li>
</ul>

<br/>

Можно вкладывать операторы IF внутрь других операторов IF.
