require 'pg'

task :setup do
  connection = PG.connect
  connection.exec('DROP DATABASE if exists crc_workshop;')
  connection.exec('CREATE DATABASE crc_workshop;')

  connection = PG.connect :dbname => 'crc_workshop';

  connection.exec('CREATE TABLE cohort (id SERIAL PRIMARY KEY, name VARCHAR(20))')

  connection.exec('CREATE TABLE student (id SERIAL PRIMARY KEY, name VARCHAR(20),
   image_url VARCHAR(20), cohort_id integer REFERENCES student(id));')

  connection.exec('CREATE TABLE tag (id SERIAL PRIMARY KEY, name VARCHAR(20))')

  connection.exec('CREATE TABLE student_tag (id SERIAL PRIMARY KEY,
    student_id integer REFERENCES student(id),
    tag_id integer REFERENCES tag(id))')

end

task :seed_db do
  connection = PG.connect :dbname => 'crc_workshop';
  connection.exec ('TRUNCATE TABLE student_tag CASCADE;')
  connection.exec ('TRUNCATE TABLE cohort CASCADE;')
  connection.exec ('TRUNCATE TABLE student CASCADE;')
  connection.exec ('TRUNCATE TABLE tag CASCADE;')
  connection.exec ("INSERT INTO student values (1, 'alice', 'image', 1);")
  connection.exec ("INSERT INTO student values (2, 'bob', 'image', 1);")
  connection.exec ("INSERT INTO student values (3, 'cat', 'image', 1);")
  connection.exec ("INSERT INTO student values (4, 'dean', 'image', 2);")
  connection.exec ("INSERT INTO student values (5, 'ellie', 'image', 2);")
  connection.exec ("INSERT INTO cohort values (1, 'oct')")
  connection.exec ("INSERT INTO cohort values (2, 'may')")
  connection.exec ("INSERT INTO tag values (1, 'green-tdd')")
  connection.exec ("INSERT INTO tag values (2, 'bgl')")
  connection.exec ("INSERT INTO student_tag values (1,1,1)")
  connection.exec ("INSERT INTO student_tag values (2,1,2)")
  connection.exec ("INSERT INTO student_tag values (3,2,1)")

end
