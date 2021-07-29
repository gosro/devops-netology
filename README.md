# netology
I'll commit my homework here
## Разработка
1. Полсе написания кода Разработчики должны написать тесты(юнит, функциональные, приемочные)
2. После комитмента, код поподает в git, потом билдим код и уже отправляем в jenkins, если у меня настроен пайп то уже юнит сам добавится и протестирует приложение
3. после тестирования отрпавляем в продакшен, сначала поговорив с менеджером и с разработчиками что они думают.
4. После того когда они убедятся что на тестовой среде все работает, отправляем в релиз и деплоем контейнер на  среду прод

changed2

Changes:

 Local .terraform directories

 .tfstate files

 Crash log files

 Exclude all .tfvars files, which are likely to contain sentitive data, such as
 password, private keys, and other secrets. These should not be part of version 
 control as they are data points which are potentially sensitive and subject 
 to change depending on the environment.

  Ignore override files as they are usually used to override resources locally and so
   are not checked in

Include override files you do wish to add to version control using negated pattern

 !example_override.tf

 Include tfplan files to ignore the plan output of command: terraform plan -out=tfplan
 example: *tfplan*

 Ignore CLI configuration files