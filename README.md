# 7-1-IaC

# 7.1. Инфраструктура как код

##  Задача 1. Выбор инструментов.

Какой тип инфраструктуры будем использовать для этого проекта: изменяемый или не изменяемый?

Предподчтение к не изменяемому типу инфраструктуры. Так как есть момент в задании - "техническое задание еще не четкое, что приведет к большому количеству небольших релизов, тестирований интеграций, 
откатов, доработок, то есть скучно не будет." В случае неизменяемой архитектуры не потребуется отслеживать историческую ситуацию.
Да и в принципе, этот вариант с точки зрения оператионс на мой взгляд менее трудозатратный.

Будет ли центральный сервер для управления инфраструктурой?

Мой подход нет, не будет центрального серверауправления конфигурацией. 
Центральный сервер - это дополнительная инфраструктура - которая требует дополнительных ресурсов и 
как аппаратно програмных так и специалистов, единая точка отказа, дополнительный риск с точки зрения безопасности. 


Будут ли агенты на серверах?

Нет. Отсутствие агентов упрощает жизнь системным администраторам, плюс нередко
насистемах уже стоят агенты Касперского, DLP, и др., которые не редко онфликтуют с другими агентами.


Будут ли использованы средства для управления конфигурацией или инициализации ресурсов?

Да, для управления конфигураций среди существующих под данные требования подходит Ansible.
Для инициализации ресурсов уже есть Terraform, который год назад начали активно использовать.
Для развёртывания образов Docker, тем более что разработчики привыкли его использовать 
и есть большая база Kubernetes конфигураций,

##  Задача 2. Установка терраформ.

На рабочем ноутбуку с Win10

    C:\Users\Lenovo>
    C:\Users\Lenovo>terraform --version
    Terraform v1.0.8
    on windows_amd64

    C:\Users\Lenovo>


##  Задача 3. Поддержка легаси кода.

На ВМ Вагрант Ubuntu

Использовал рекомендации

https://stackru.com/questions/54206238/kak-ustanovit-neskolko-ili-dve-versii-terraform


    vagrant@vagrant:/usr/local/tf/12$ terraform11 --version
    Terraform v0.11.14
    
    Your version of Terraform is out of date! The latest version
    is 1.0.8. You can update by downloading from www.terraform.io/downloads.html
    
    
    vagrant@vagrant:/usr/local/tf/12$ terraform12 --version
    Terraform v0.12.20
    
    Your version of Terraform is out of date! The latest version
    is 1.0.8. You can update by downloading from https://www.terraform.io/downloads.html
    vagrant@vagrant:/usr/local/tf/12$

