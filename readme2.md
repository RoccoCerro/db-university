### 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

  SELECT *
  FROM `students`
  INNER JOIN `degrees`
  ON `students`.`degree_id` = `degrees`.`id`
  WHERE `degrees`.`name` = "Corso di laurea in economia";

###  2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

  SELECT `degrees`.*, `departments`.`name` AS "name_department"
  FROM `departments`
  INNER JOIN `degrees`
  ON `degrees`.`department_id` = `departments`.`id`
  WHERE `degrees`.`name` LIKE 'Corso di laurea magistrale%' AND `departments`.`name` = "dipartimento di Neuroscienze";

### 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

  SELECT `teachers`.`name`, `teachers`.`surname`, `courses`.*, `course_teacher`.*
  FROM `teachers`
  INNER JOIN `course_teacher`
  ON `teachers`.`id` = `course_teacher`.`teacher_id`
  INNER JOIN `courses`
  ON `courses`.`id` = `course_teacher`.`course_id`
  WHERE `teachers`.`name` = "Fulvio" AND `teachers`.`surname` = "amato";