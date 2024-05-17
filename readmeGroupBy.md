### 1. Contare quanti iscritti ci sono stati ogni anno

  SELECT YEAR(enrolment_date) as anno, COUNT(*) as numero_iscritti 
  FROM `students` 
  GROUP BY YEAR(enrolment_date);