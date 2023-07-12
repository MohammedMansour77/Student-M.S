<?php

namespace StudentManagement;

class Student {
    public $id;
    public $name;
    public $email;
    public $courses = array();
}

class Course {
    public $id;
    public $name;
}

trait Loggable {
    public function log($message) {
        echo $message . "\n";
    }
}

class Manager {
    use Loggable;

    private $students = array();

    public function addStudent(Student $student) {
        $this->students[] = $student;
        $this->log("Added student with ID: " . $student->id);
    }

    public function getStudentById($id) {
        foreach ($this->students as $student) {
            if ($student->id == $id) {
                return $student;
            }
        }
        return null;
    }

    public function updateStudent(Student $student) {
        foreach ($this->students as &$s) {
            if ($s->id == $student->id) {
                $s = $student;
                break;
            }
        }
        $this->log("Updated student with ID: " . $student->id);
    }

    public function deleteStudent(Student $student) {
        foreach ($this->students as $key => &$s) {
            if ($s->id == $student->id) {
                unset($this->students[$key]);
                break;
            }
        }
        $this->log("Deleted student with ID: " . $student->id);
    }
}

$manager = new Manager();

$student1 = new Student();
$student1->id = 1;
$student1->name = "John Doe";
$student1->email = "johndoe@example.com";

$course1 = new Course();
$course1->id = 1;
$course1->name = "Mathematics";

$course2 = new Course();
$course2->id = 2;
$course2->name = "Science";

$student1->courses[] = $course1;
$student1->courses[] = $course2;

$manager->addStudent($student1);

$foundStudent = $manager->getStudentById(1);
echo "Found student: " . print_r($foundStudent, true) . "\n";

$foundStudent->name = "Jane Doe";
$manager->updateStudent($foundStudent);

$deletedStudent = clone($foundStudent);
$manager->deleteStudent($deletedStudent);

?>
