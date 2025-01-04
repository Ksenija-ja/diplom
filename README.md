Процедура запуска авто-тестов 

Перед запуском авто-тестов необходимо проверить наличие программ и установить при отсутствии:

	  IntelliJ IDEA
   
	  Docker Desktop
   
    Google Chrome 
    
	  GitHub
   
Запуск авто-тестов:

1.	Открыть проект в IntelliJ IDEA
2.	Запустить Docker Desktop
3.	Запустить контейнеры СУБД MySQl, PostgerSQL и Node.js командой в терминале: docker compose up
4. Запустить SUT в терминале при помощи команды:
   
	для MySQL:

java "-Dspring.datasource.url=jdbc:mysql://localhost:3306/app" -jar artifacts/aqa-shop.jar

	для PostgreSQL:
 
java "-Dspring.datasource.url=jdbc:postgresql://localhost:5432/app" -jar artifacts/aqa-shop.jar

5.Приложение должно быть доступно по адресу: http://localhost:8080/

6.Запуск тестов:

	для MySQL: gradlew clean test "-Ddb.url=jdbc:mysql://localhost:3306/app"
 
	для PostgreSQL:  gradlew clean test "-Ddb.url=jdbc:postgresql://localhost:5432/app"
 
7. Сгенерировать отчет командой в новом терминале: gradlew allureServe
  
     Автоматически откроется отчет в браузере.
   
Для остановки приложения в окне терминала нужно ввести команду Ctrl+С 
