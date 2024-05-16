### 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

  SELECT *
  FROM `students`
  INNER JOIN `degrees`
  ON `students`.`degree_id` = `degrees`.`id`
  WHERE `degrees`.`name` = "Corso di laurea in economia";

  2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
  Neuroscienze

  SELECT `degrees`.*, `departments`.`name` AS "name_department"
  FROM `departments`
  INNER JOIN `degrees`
  ON `degrees`.`department_id` = `departments`.`id`
  WHERE `degrees`.`name` LIKE 'Corso di laurea magistrale%' AND `departments`.`name` = "dipartimento di Neuroscienze";