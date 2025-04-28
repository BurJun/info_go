package main

import (
	"fmt"
	"regexp"
)

func main() {

	/*----------------*/
	/* Изучение пакета regexp */
	/*----------------*/
	re := regexp.MustCompile(`\d+`) /*ищем 1 или более цифр*/
	text := "У меня есть 3 яблока и 12 слив"
	number := re.FindAllString(text, -1) /* -1 = без ограничений в еол-ве*/
	fmt.Println(number)

	/*Проверка почты на правильность*/
	/*Прерка есть ли текст до @, потом домен и потом суффикс (например: .ru)*/
	re2 := regexp.MustCompile(`^[\w._%+-]+@[\w.-]+\.[a-zA-Z]{2,}$`)
	email := "test@mail.ru"

	if re2.MatchString(email) {
		fmt.Println("Email пошел проверку!")
	} else {
		fmt.Println("Ошибка")
	}

	/*Замена слова*/
	re3 := regexp.MustCompile(`кот`)
	text2 := "Мой кот спит на диване"

	resualt := re3.ReplaceAllString(text2, "собака")
	fmt.Println(resualt)
}
