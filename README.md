## Задача: ##  
Исследуются данные о работе некоторого образовательного сервиса.
В ходе A/B тестирования одной гипотезы **целевой группе была предложена новая механика оплаты услуг на сайте, у контрольной группы оставалась базовая механика**. Необходимо *проанализировать итоги эксперимента* (и сделать вывод, стоит ли запускать новую механику оплаты на всех пользователей), *написать функции обновления данных*, пересчета метрик и визуализации результатов, а также *с помощью SQL-запросов рассчитать продуктовые метрики и число лояльных* (очень усердных) студентов.  

## Стек: ##  
pandas, numpy, seaborn, matplotlib, tqdm, scipy, airflow, SQL  

## Реализация: ##  
1. Проведен EDA,
2. Проведен анализ пользовательской активности и оплат,  
3. Оценены метрики платящих активных и неактивных пользователей,
4. Расчитаны метрики CR / ARPAU / ARPPU для тестовых групп,
5. Проверены гипотезы о нормальном распределении метрик,
6. Проверены гипотезы об отстутствии различий в метриках между тестом и контролем,  
7. Написан SQL запрос на выдачу наиболее активных студентов (решено 20 задач за месяц),
8. Написан SQL запрос на выдачу метрик ARPU (по всем пользователям), ARPAU (по пользователям, решившим больше 10 задач правильно в любых дисциплинах), CR в покупку по всем пользователям, СR активного пользователя в покупку, CR пользователя из активности по математике в покупку курса по математике
9. Написан даг для обновления данных и пересчета метрик и функция визуализации результатов (airflow)

## Результат: ##  
В ходе исследования возникли моменты, требующие уточнения (оплаты неактивных юзеров, а также система сплитования в общем). Однако, при условии верности входных данных, выяснилось, что если пользователь платит - он платит статистически значимо больше и новая механика оплаты может быть расширена на всех пользователей (после уточнения возникших вопросов)

## Описание данных ##  
- groups.csv - файл с информацией о принадлежности пользователя к контрольной или экспериментальной группе (А – контроль, B – целевая группа) 
- groups_add.csv - дополнительный файл с пользователями, который вам прислали спустя 2 дня после передачи данных  
- active_studs.csv - файл с информацией о пользователях, которые зашли на платформу в дни проведения эксперимента 
- checks.csv - файл с информацией об оплатах пользователей в дни проведения эксперимента.

