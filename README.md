## Performance Testing Results

### Endpoint `/all-student`
#### GUI Result
![JMeter GUI - all-student](assets/images/test_plan_all_student.png)

#### CLI Result
![JMeter CLI - all-student](assets/images/test_plan_all_student_jtl.png)

### Endpoint `/all-student-name`
#### GUI Result
![JMeter GUI - all-student-name](assets/images/test_plan_all_student_name.png)

#### CLI Result
![JMeter CLI - all-student-name](assets/images/test_plan_all_student_name_jtl.png)

### Endpoint `/highest-gpa`
#### GUI Result
![JMeter GUI - highest-gpa](assets/images/test_plan_highest_gpa.png)

#### CLI Result
![JMeter CLI - highest-gpa](assets/images/test_plan_highest_gpa_jtl.png)

## Hasil JMeter Setelah Optimasi

### Endpoint `/all-student`
![Setelah optimasi - all-student](assets/images/final_all_student.png)

### Endpoint `/all-student-name`
![Setelah optimasi - all-student-name](assets/images/final_all_student_name.png)

### Endpoint `/highest-gpa`
![Setelah optimasi - highest-gpa](assets/images/final_highest_gpa.png)

## Kesimpulan
Setelah dilakukan optimasi, ketiga endpoint menunjukkan peningkatan performa yang signifikan, jauh melampaui target 20%:
- `/all-student`: meningkat ~93% (86335ms → 6308ms) dengan menghilangkan N+1 query problem menggunakan `studentCourseRepository.findAll()`
- `/all-student-name`: meningkat ~96% (3647ms → 142ms) dengan mengganti string concatenation menggunakan `Collectors.joining()`
- `/highest-gpa`: meningkat ~97% (855ms → 29ms) dengan menggunakan query level database melalui `findTopByOrderByGpaDesc()`

