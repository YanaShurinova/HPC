# Bilateral

## Ссылка на google colab
https://colab.research.google.com/drive/1vSuQeiN-xynYKB5_4cLgnNJY3eJHMnze?usp=sharing

## Входное изображение
![image.bmp](https://github.com/YanaShurinova/HPC/blob/main/SaltAndPeper/image.bmp)

## Изображение после обработки на CPU и GPU
![CPU.bmp](https://github.com/YanaShurinova/HPC/blob/main/SaltAndPeper/CPU.bmp)
![GPU.bmp](https://github.com/YanaShurinova/HPC/blob/main/SaltAndPeper/GPU.bmp)

## Описание реализации
Одна нить обрабатывает один пиксель => Общее число нитей = общему числу пикселей, каждая из которых 
принимает kernel_size^2 (размер фильтра=9) пикселей и сохраняет значение медианы в выходной массив.
Изображение грузится в текстуру как двумерный массив(матрица).

Из результатов экспериментов ниже, отчетливо видно, что использование параллельной программы даже для
обработки изображений малого размера дает ускорение более, чем в 100 раз.
Рост времени программы на CPU носит экспоннциальный характер, в то время как рост времени программы на CPU носит 
~ логарифмический.

### Таблица с данными об эксперименте
| Размер изображения  | Время выполнения на CPU  | Время выполнения на GPU| Ускорение |
|:------------------- |:------------------------:|:----------------------:| ---------:|
| 50х50               | 0,09367                  | 0,00067                | 138,69    |
| 100х100             | 0,3827                   | 0,000849               | 450,70    |
| 200х200             | 2,1087                   | 0,001903               | 1107,68   |
| 400х400             | 6,48                     | 0,0056                 | 1149,46   |
| 800х800             | 27,80339                 | 0,0226                 | 1228,06   |
| 1600х1600           | 110,073                  | 0,07462                | 1475,014  |


### Графики
![usc.png](https://raw.githubusercontent.com/YanaShurinova/HPC/main/SaltAndPeper/usc.png)
![time.png](https://raw.githubusercontent.com/YanaShurinova/HPC/main/SaltAndPeper/time.png)
