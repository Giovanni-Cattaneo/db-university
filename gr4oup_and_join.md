
## Group by

Contare quanti iscritti ci sono stati ogni anno
SELECT YEAR(`enrolment_date`)
COUNT(*)
FROM students
GROUP BY YEAR(`enrolment_date`)
ORDER BY YEAR(`enrolment_date`);

Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT `office_address`, COUNT(id) 
FROM `teachers` 
GROUP BY `office_address`;

Calcolare la media dei voti di ogni appello d'esame
SELECT `exam_id`, AVG(`vote`)
FROM `exam_student`
GROUP BY `exam_id`;

Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT `department_id`, COUNT(*)
FROM `degrees`
GROUP BY `department_id`;

## Joins

Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT *
FROM `students`
INNER JOIN `degrees`
ON `degrees`.`id` = 53;

Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT *
FROM `degrees`
INNER JOIN `departments`
ON `departments`.`name` = 'Dipartimento di Neuroscienze' AND `degrees`.`level`= "magistrale";

Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT * 
FROM `courses`
INNER JOIN `teachers`
ON `teachers`.`id` = 44;

Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
SELECT *
FROM `degrees`
INNER JOIN `courses` ON `courses`.`degree_id` = `degrees`.`id`
INNER JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`course_id`;

Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.