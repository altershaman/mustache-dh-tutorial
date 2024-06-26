# Корневой контекст

В этом уроке разбираем что **код презентации** может передать в файл-шаблон(просто шаблон) в качестве **корневого контекста** для mustache \{\{.\}\}.

- Простые значения:
  - строковые
  - численные
  - булевы
  - null
- Объекты
- Массивы

Контекст может быть "пустым" (empty):
 - \"\"
 - 0
 - false
 - null
 - []

 ###### Интерполяция 
 ###### **\{\{.\}\}**
 
---
{{.}}

---

### Задание "Формирование и интерполяция корневого контекста"

  * Откройте для редактирования файл mustache/presentations.yaml
  * Найдите участок кода, отвечающий за формирование данной презентации
    ```yaml

    entities:
      noname:
        presentations:

          root_context:
            type: markdown
            template: templates/root_context.md
            source: > # код презентации
              ( 
                "какое-то строковое значение"
              )
    ```
  * В примере мы передаем в шаблон (данный шаблон) непустой контекст, содержащий простое строковое значение.
  *Контекст может быть передан в виде значения переменной JSONata, например `($result:= "какое-то строковое значение")` -- контекст не изменится.*
  * Найдите в файле-шаблоне раздел "Интерполяция". Mustache \{\{.\}\} интерполирует текущий контекст
  * Измените код презентации так, чтобы контекст был:
    * `123` - интерполируется успешно
    * `0` -  интерполируется пустое значение
    * `"0"` -  интерполируется успешно
    * `""` -  интерполируется пустое значение
    * `true` - интерполируется успешно
    * `false` -  интерполируется пустое значение
    * `null` -  интерполируется пустое значение
    * `{"key": "value"}` - интерполируется как вложенный контекст `[object Object]`
    * `{}` - интерполируется как вложенный контекст `[object Object]`
    * `[1,2,3]` -  интерполируется успешно
    * `[]` -  интерполируется пустое значение


### Take away
1. Mustache принимает на вход результат выполнения кода презентации -- это корневой контекст
1. Mustache \{\{.\}\} интерполирует **значение** текущего контекста (в данном уроке мы пока рассмотрели только корневой контекст)
1. Непустые строковые значения, ненулевые численные значения, `true`, непустые массивы интерполируются как есть
1. объекты (в том числе пустые `{}`) интерполируются как `[object Object]` -- вложенные контексты, требующие более гранулярного подхода
1. `0`, `false`, `null`, `[]` не интерполируются

