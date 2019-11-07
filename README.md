### Example Database structure

From this workshop: https://github.com/makersacademy/skills-workshops/tree/master/week-4/domain_modelling_student_directory_using_crc_cards

#### Set up
- bundle
- rake setup
- rake seed_db

#### Querying
- psql
- c \crc_workshop
- `select * from student join cohort on cohort.id=student.cohort_id;`
