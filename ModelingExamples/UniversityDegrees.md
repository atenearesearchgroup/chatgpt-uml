# University Degrees

## Context

We want to model the educational system of universities offering different undergraduate and graduate degrees (masters), according to the following specifications. 

*	Each degree is composed of a set of subjects, each with several ECTS credits, which are taught every academic year. 
*	The same subject can only be taught once each academic year. 
*	Each subject only belongs to one University, although it can be part of several of its degrees (both bachelor's and master's).
*	Each subject is taught by a single lecturer, which may vary from year to year. 
*	Each lecturer may not teach more than 4 subjects each year (regardless of their number of credits).
*	Each year the lecturers evaluate the students enrolled in the subjects they teach, assigning them a grade between 0 and 10 (we assume that there are no "no-shows", but that all enrolled students obtain a grade between 0 and 10). A grade of 5 or higher is considered a passing grade. 
*	The same student can only register up to 3 times for the same subject, in different years. 
*	A student may only pass a subject once and cannot register for subjects already passed. 
*	For the sake of simplicity, we will assume that each subject has only one exam per academic year. 
*	All subjects must be evaluated before the end of the academic year they are taught. 
*	Teachers cannot enroll in the subjects they teach in that course, although they can enroll in other subjects. 
*	To obtain a diploma at a university, a student needs to pass at least 240 credits of the subjects in case of undergraduate degrees or 60 for graduate degrees. 
*	The diploma includes the name of the university and the name of the degree, as well as the year in which the student passed the last subject that completed the necessary credits. 
*	A person can obtain as many diplomas as degrees a university offers if he or she completes the corresponding courses. 
*	Finally, to be able to enroll in a subject that is taught only at the postgraduate level, the student must hold an undergraduate diploma (from that university or from another one).

## Questions

1. Develop a UML class diagram with the structure of such a system, with all the elements mentioned above, the relationships between them, and all required integrity constraints. 
2.	Model the behavior of the system, defining the necessary operations to model the following actions, including their pre- and post-conditions: 
    * A student enrolls one year in one subject of a degree. 
    * A lecturer grades a student enrolled in one of the subjects he teaches. 
    * A student applies for a diploma.
 
