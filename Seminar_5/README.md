#Урок 5. Docker Compose и Docker Swarm
Скрыть
1) создать сервис, состоящий из 2 различных контейнеров: 1 - веб, 2 - БД (compose)
Задание со звездочкой - повышенной сложности..
** не обязательно 2) необходимо создать 3 сервиса в каждом окружении (dev, prod, lab)
** не обязательно 3) по итогу на каждой ноде должно быть по 2 работающих контейнера
4) выводы зафиксировать


#Термины

Для того чтобы пользоваться swarm, надо запомнить несколько типов сущностей:

Node - это наши виртуальные машины, на которых установлен docker. Есть manager и workers ноды. Manager нода управляет workers нодами. Она отвечает за создание/обновление/удаление сервисов на workers, а также за их масштабирование и поддержку в требуемом состоянии. Workers ноды используются только для выполнения поставленных задач и не могут управлять кластером.

Stack - это набор сервисов, которые логически связаны между собой. По сути это набор сервисов, которые мы описываем в обычном compose файле. Части stack (services) могут располагаться как на одной ноде, так и на разных.

Service - это как раз то, из чего состоит stack. Service является описанием того, какие контейнеры будут создаваться. Если вы пользовались docker-compose.yaml, то уже знакомы с этой сущностью. Кроме стандартных полей docker в режиме swarm поддерживает ряд дополнительных, большинство из которых находятся внутри секции deploy.

Task - это непосредственно созданный контейнер, который docker создал на основе той информации, которую мы указали при описании service. Swarm будет следить за состоянием контейнера и при необходимости его перезапускать или перемещать на другую ноду.

Создаем два ДК-файла:
   ![pic1](https://github.com/DimitryZykin/Containerisation/blob/main/Seminar_5/source/Pic2.png) 
   
Компилируем node:
   ![pic2](https://github.com/DimitryZykin/Containerisation/blob/main/Seminar_5/source/Pic4.png) 
   
Проверяем:
   ![pic3](https://github.com/DimitryZykin/Containerisation/blob/main/Seminar_5/source/Pic5.png) 

![pic4](https://github.com/DimitryZykin/Containerisation/blob/main/Seminar_5/source/Pic1.png) 
![pic5](https://github.com/DimitryZykin/Containerisation/blob/main/Seminar_5/source/Pic3.png) 
