# Компьютерная графика ФПМИ МФТИ
## Ссылки
- [Сайт с туториалами](http://www.opengl-tutorial.org/ru/)
## Домашняя работа 1
<p float="left" align="center">
  <img src="https://github.com/Khaymon/mipt-2022-computer-graphics/blob/master/homework1/triangles/Triangles.png" width="250" height="250" />
  <img src="https://github.com/Khaymon/mipt-2022-computer-graphics/blob/camera_movement/homework1/camera_movement/Triangles.gif" width="250" height="250" />
  <img src="https://github.com/Khaymon/mipt-2022-computer-graphics/blob/master/homework1/instead_of_cube/T.gif" width="250" height="250" />
</p>  

1. Запустить код уроков, проверить, что все работает, научиться создавать исполняемые файлы
2. Используя два разных шейдера, нарисовать 2 пересекающихся треугольника разных цветов с альфа-каналом (полупрозрачных), вершины которых не находятся на краях экрана
3. Добавить камеру в сцену, поиграться с функцией LookAt. Важно! После этого создать простой аналог анимационного фильма, где камера кружится вокруг тех двух треугольников, захардкодить её движение (не использовать ввод с мыши и клавиатуры)  (на ваше усмотрение, по какой траектории движется камера, какая задержка между кадрами, сколько кадров и т.п.)
4. Вместо куба из 4 урока, отрисовать любую другую объемную закрытую фигуру. Постараться настроить цвета вершин так, чтобы это было эстетично (но так как у всех понятия красоты отличаются, это не оценивается) и реализовать движение камеры вокруг.
### Оценивание домашней работы 1
На сдаче задания напротив фамилии каждого в [табличке](https://docs.google.com/spreadsheets/d/189_4597-jgIL-3nmXVoaYK-P0_RrbIyHWBmGnprwCsw/edit) будет 6 галочек:
- (1,2) Сдано задание (это значит, что я удостоверился, что у студента выполнены все пункты, описанные в части «задание») Необходимые части: исполняемый файл (.exe со всеми необходимыми для работы библиотеками внутри или в директории) и код (.сpp + файлы шейдеров). Обязательно иметь возможность показать код, описать все части приложения. Задание сдано если код работает, условия соблюдены, то же самое не было показано другим человеком ранее.
- (3) Наличие исполняемого файла для обоих заданий.
- (4,5) Сданы задачи, которые скину в выходные. Т.е. есть записанное решение задачи, объяснен ход решения, дан верный ответ в читаемом виде + дан ответ на вопрос по теории с лекций.
- (6) Доп. Балл за оригинальность / дополнительную фичу...  
Вес каждого пункта рассчитаем позже. Вес всего задания 2 балла не считая допов. Напоминаю, что для допуска на экзамен, нужно набрать не менее 1 балла.

### TODO
- [X] Треугольники
- [X] Движение камеры
- [X] Что-то вместо куба
- [X] Задачи по лекциям

## Домашняя работа 2
Создаем шутер на OpenGL
1. В нашей сцене учимся создавать объекты (те самые пирамиды- бублики-шары из 1го задания) с необходимыми позицией и ориентацией. (Пример: Instantiate ( Vector3 position, Vector3 rotation)
2. Создаем эти объекты в сцене в рандомных точках окрестности камеры (по типу не ближе 2х попугаев, но не дальше 50ти попугаев) с опреденными временными интервалами (лучше по времени (раз в несколько секунд),  но можно и по количеству прошедших кадров ( раз в n кадров) ) и рандомной ориентацией в пространстве
Поздравляю, вы создали себе врагов
Теперь создаем снаряды
3. Создаем "fireball" (не принципиально, будет ли это заранее сгенерированный 3D объект, как описывается в 7ом уроке туториала, либо сгенерированные по сфере точки, превращенные в полигоны)
4. "Натягиваем" на шар текстуру (любую вам приятную)
5. Добавляем шару возможность двигаться в направлении камеры. ( как пример: position += camera.forward × moveSpeed × deltaTime )
Порадуйтесь, что создали странноуправляемый наводящийся заряд.
6. Исправьте, чтобы каждый шар двигался в своем постоянном направлении
7. Каждому объекту добавляем "коллайдер". Определенное расстояние в попугаях (радиус сферы),которое мы используем для просчета соприкосновения объектов. Т.е. для всех наших снарядов попарно проверяем, что расстояния между центрами объектов меньше суммы радиусов коллайдеров (Пример: if ( Math.abs ( object.position - fireball.position ) < object.colliderRadius + fireball.colliderRadius )  object.delete(); )
8. При взаимодействии объектов, удаляем оба объекта

### На допополнительный балл
- Убираем весь свет в сцене, делаем источником света fireball-ы
- показываем на экране кол-во сбитых объектов
Супердопбалл: добавляем возможность сохранить и загрузить состояние нашей сцены (при нажатии определенной кнопки, сохраняем все необходимые данные объектов в текстовый файл, при нажатии другой, из него загружаем эти данные.
