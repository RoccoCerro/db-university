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

### 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

  SELECT `students`.`surname`, `students`.`name`, `degrees`.*, `departments`.`name`
  FROM `students`
  INNER JOIN `degrees`
  ON `students`.`degree_id` = `degrees`.`id`
  INNER JOIN `departments`
  ON `degrees`.`department_id` = `departments`.`id`
  ORDER BY `students`.`surname`, `students`.`name` ASC;

### 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

  SELECT `courses`.*, `degrees`.`name`, `teachers`.`name`
  FROM `courses`
  INNER JOIN `degrees`
  ON `courses`.`degree_id` = `degrees`.`id`
  INNER JOIN `course_teacher`
  ON `course_teacher`.`course_id` = `courses`.`id`
  INNER JOIN `teachers`
  ON `course_teacher`.`teacher_id` = `teachers`.`id`

### 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

  SELECT `teachers`.*, `departments`.`name`
  FROM `courses`
  INNER JOIN `degrees`
  ON `courses`.`degree_id` = `degrees`.`id`
  INNER JOIN `course_teacher`
  ON `course_teacher`.`course_id` = `courses`.`id`
  INNER JOIN `teachers`
  ON `course_teacher`.`teacher_id` = `teachers`.`id`
  INNER JOIN `departments`
  ON `degrees`.`department_id` = `departments`.`id`
  WHERE `departments`.`name` = "dipartimento di matematica";