# Go для начинающих

Практический курс по языку Go. Никакой теории ради теории — только то, что реально нужно, чтобы писать рабочий код.

---

## Что нужно перед стартом

- Установи Go: [go.dev/dl](https://go.dev/dl/) (версия 1.21+)
- Редактор: VSCode с расширением `golang.go` или GoLand
- Проверь установку: `go version` в терминале

---

## Модуль 1. Первая программа

Создай папку проекта и инициализируй модуль:

```bash
mkdir hello && cd hello
go mod init hello
```

Файл `main.go`:

```go
package main

import "fmt"

func main() {
    fmt.Println("Привет, Go!")
}
```

```bash
go run main.go
```

**Что здесь важно:**
- `package main` — точка входа в программу
- `func main()` — функция, с которой всё начинается
- `import` — подключение пакетов из стандартной библиотеки

**Задание:** выведи своё имя и текущий год.

---

## Модуль 2. Переменные и типы

```go
package main

import "fmt"

func main() {
    // Три способа объявить переменную
    var name string = "Алексей"
    var age int = 25
    score := 99.5 // короткое объявление, тип выводится автоматически

    fmt.Println(name, age, score)

    // Константа
    const pi = 3.14159
    fmt.Println(pi)
}
```

**Основные типы:** `int`, `float64`, `string`, `bool`, `byte`, `rune`

**Нулевые значения** — переменная без присвоения не мусор, а ноль: `0` для чисел, `""` для строк, `false` для булевых.

**Задание:** объяви переменные для описания фильма (название, год, рейтинг) и выведи их в одну строку.

---

## Модуль 3. Условия и циклы

```go
package main

import "fmt"

func main() {
    x := 42

    // if-else
    if x > 100 {
        fmt.Println("большое")
    } else if x > 10 {
        fmt.Println("среднее")
    } else {
        fmt.Println("маленькое")
    }

    // for — единственный цикл в Go
    for i := 0; i < 5; i++ {
        fmt.Println(i)
    }

    // while-стиль
    n := 1
    for n < 100 {
        n *= 2
    }
    fmt.Println(n)

    // range по строке
    for i, ch := range "Go!" {
        fmt.Printf("%d: %c\n", i, ch)
    }
}
```

**Switch в Go** не проваливается по умолчанию (не нужен `break`):

```go
day := "понедельник"
switch day {
case "суббота", "воскресенье":
    fmt.Println("выходной")
default:
    fmt.Println("рабочий день")
}
```

**Задание:** напиши программу, которая выводит числа от 1 до 20, заменяя кратные 3 на "Fizz", кратные 5 на "Buzz", кратные обоим — на "FizzBuzz".

---

## Модуль 4. Функции

```go
package main

import (
    "fmt"
    "math"
)

// Функция с двумя возвращаемыми значениями
func divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, fmt.Errorf("деление на ноль")
    }
    return a / b, nil
}

// Вариадическая функция
func sum(nums ...int) int {
    total := 0
    for _, n := range nums {
        total += n
    }
    return total
}

// Функция как значение
func apply(x float64, fn func(float64) float64) float64 {
    return fn(x)
}

func main() {
    result, err := divide(10, 3)
    if err != nil {
        fmt.Println("Ошибка:", err)
    } else {
        fmt.Printf("%.2f\n", result)
    }

    fmt.Println(sum(1, 2, 3, 4, 5))

    // Анонимная функция
    double := func(x float64) float64 { return x * 2 }
    fmt.Println(apply(5, double))
    fmt.Println(apply(9, math.Sqrt))
}
```

**Паттерн `(result, error)`** — главный способ обработки ошибок в Go. Не исключения, а явные возвращаемые значения.

**Задание:** напиши функцию `minMax(nums []int) (int, int)`, которая возвращает минимум и максимум из среза.

---

## Модуль 5. Массивы, срезы, карты

```go
package main

import "fmt"

func main() {
    // Массив — фиксированный размер
    arr := [3]int{1, 2, 3}
    fmt.Println(arr)

    // Срез — динамический, используется повсеместно
    nums := []int{10, 20, 30}
    nums = append(nums, 40, 50)
    fmt.Println(nums)
    fmt.Println(nums[1:3]) // срез [20, 30]

    // make для создания среза с нужной ёмкостью
    buf := make([]byte, 0, 64)
    buf = append(buf, "hello"...)
    fmt.Println(string(buf))

    // Карта (map)
    scores := map[string]int{
        "Алексей": 95,
        "Мария":   88,
    }
    scores["Иван"] = 72

    for name, score := range scores {
        fmt.Printf("%s: %d\n", name, score)
    }

    // Проверка наличия ключа
    val, ok := scores["Пётр"]
    if !ok {
        fmt.Println("Пётр не найден, val =", val)
    }
}
```

**Задание:** получи список слов, подсчитай частоту каждого слова и выведи результат.

---

## Модуль 6. Структуры и методы

```go
package main

import (
    "fmt"
    "math"
)

type Point struct {
    X, Y float64
}

// Метод с получателем-значением
func (p Point) String() string {
    return fmt.Sprintf("(%.1f, %.1f)", p.X, p.Y)
}

// Метод с указателем — может изменять структуру
func (p *Point) Scale(factor float64) {
    p.X *= factor
    p.Y *= factor
}

func (p Point) Distance(other Point) float64 {
    dx := p.X - other.X
    dy := p.Y - other.Y
    return math.Sqrt(dx*dx + dy*dy)
}

type Rectangle struct {
    TopLeft     Point
    BottomRight Point
}

func (r Rectangle) Area() float64 {
    w := math.Abs(r.BottomRight.X - r.TopLeft.X)
    h := math.Abs(r.BottomRight.Y - r.TopLeft.Y)
    return w * h
}

func main() {
    p := Point{3, 4}
    fmt.Println(p)
    p.Scale(2)
    fmt.Println(p)

    origin := Point{0, 0}
    fmt.Printf("Расстояние: %.2f\n", p.Distance(origin))

    rect := Rectangle{Point{0, 0}, Point{5, 3}}
    fmt.Printf("Площадь: %.1f\n", rect.Area())
}
```

**Задание:** создай структуру `BankAccount` с методами `Deposit`, `Withdraw` (с проверкой баланса) и `Balance`.

---

## Модуль 7. Интерфейсы

```go
package main

import (
    "fmt"
    "math"
)

type Shape interface {
    Area() float64
    Perimeter() float64
}

type Circle struct {
    Radius float64
}

func (c Circle) Area() float64      { return math.Pi * c.Radius * c.Radius }
func (c Circle) Perimeter() float64 { return 2 * math.Pi * c.Radius }

type Rect struct {
    W, H float64
}

func (r Rect) Area() float64      { return r.W * r.H }
func (r Rect) Perimeter() float64 { return 2 * (r.W + r.H) }

func printShape(s Shape) {
    fmt.Printf("Площадь: %.2f, Периметр: %.2f\n", s.Area(), s.Perimeter())
}

func main() {
    shapes := []Shape{
        Circle{Radius: 5},
        Rect{W: 4, H: 6},
    }
    for _, s := range shapes {
        printShape(s)
    }
}
```

**Интерфейсы в Go — неявные.** Тип реализует интерфейс, просто имея нужные методы. Никаких `implements`.

**Задание:** добавь тип `Triangle` и реализуй для него интерфейс `Shape`.

---

## Модуль 8. Обработка ошибок

```go
package main

import (
    "errors"
    "fmt"
)

type ValidationError struct {
    Field   string
    Message string
}

func (e *ValidationError) Error() string {
    return fmt.Sprintf("поле %s: %s", e.Field, e.Message)
}

func validateAge(age int) error {
    if age < 0 {
        return &ValidationError{Field: "age", Message: "не может быть отрицательным"}
    }
    if age > 150 {
        return &ValidationError{Field: "age", Message: "нереалистичное значение"}
    }
    return nil
}

func processUser(age int) error {
    if err := validateAge(age); err != nil {
        return fmt.Errorf("processUser: %w", err)
    }
    return nil
}

func main() {
    err := processUser(-5)
    if err != nil {
        fmt.Println(err)

        var valErr *ValidationError
        if errors.As(err, &valErr) {
            fmt.Printf("Проблемное поле: %s\n", valErr.Field)
        }
    }
}
```

**Три правила обработки ошибок:**
- Проверяй ошибку сразу после вызова функции
- Оборачивай с `fmt.Errorf("%w", err)`, чтобы не терять контекст
- Используй `errors.As` / `errors.Is` для проверки конкретных типов

**Задание:** напиши парсер конфига из строки вида `key=value` с валидацией и собственным типом ошибки.

---

## Модуль 9. Горутины и каналы

```go
package main

import (
    "fmt"
    "sync"
    "time"
)

func worker(id int, wg *sync.WaitGroup) {
    defer wg.Done()
    fmt.Printf("Воркер %d начал работу\n", id)
    time.Sleep(time.Millisecond * 100)
    fmt.Printf("Воркер %d завершил\n", id)
}

func generate(nums ...int) <-chan int {
    out := make(chan int)
    go func() {
        for _, n := range nums {
            out <- n
        }
        close(out)
    }()
    return out
}

func square(in <-chan int) <-chan int {
    out := make(chan int)
    go func() {
        for n := range in {
            out <- n * n
        }
        close(out)
    }()
    return out
}

func main() {
    var wg sync.WaitGroup
    for i := 1; i <= 3; i++ {
        wg.Add(1)
        go worker(i, &wg)
    }
    wg.Wait()
    fmt.Println("Все воркеры завершили работу")

    nums := generate(2, 3, 4, 5)
    squares := square(nums)
    for n := range squares {
        fmt.Println(n)
    }
}
```

**Горутина** — не поток ОС, а лёгкая сопрограмма. Запускай тысячи без проблем.

**Канал** — безопасный способ передать данные между горутинами. Помни: `close` вызывает отправитель, а не получатель.

**Задание:** реализуй пул воркеров — N горутин читают задачи из общего канала и обрабатывают их.

---

## Модуль 10. Select и таймауты

```go
package main

import (
    "context"
    "fmt"
    "time"
)

func slowOperation(ctx context.Context) (string, error) {
    result := make(chan string, 1)
    go func() {
        time.Sleep(200 * time.Millisecond)
        result <- "готово"
    }()

    select {
    case res := <-result:
        return res, nil
    case <-ctx.Done():
        return "", ctx.Err()
    }
}

func main() {
    ctx, cancel := context.WithTimeout(context.Background(), 100*time.Millisecond)
    defer cancel()

    res, err := slowOperation(ctx)
    if err != nil {
        fmt.Println("Таймаут:", err)
    } else {
        fmt.Println("Результат:", res)
    }

    ctx2, cancel2 := context.WithTimeout(context.Background(), 500*time.Millisecond)
    defer cancel2()

    res, err = slowOperation(ctx2)
    if err != nil {
        fmt.Println("Ошибка:", err)
    } else {
        fmt.Println("Результат:", res)
    }
}
```

**Задание:** напиши функцию, которая параллельно делает запросы к нескольким URL и возвращает результат первого успешного ответа.

---

## Модуль 11. Работа с JSON и HTTP

```go
package main

import (
    "encoding/json"
    "fmt"
    "net/http"
    "time"
)

type User struct {
    ID       int    `json:"id"`
    Name     string `json:"name"`
    Email    string `json:"email,omitempty"`
    Password string `json:"-"`
}

func usersHandler(w http.ResponseWriter, r *http.Request) {
    users := []User{
        {ID: 1, Name: "Алексей", Email: "alex@example.com"},
        {ID: 2, Name: "Мария"},
    }
    w.Header().Set("Content-Type", "application/json")
    json.NewEncoder(w).Encode(users)
}

func createUserHandler(w http.ResponseWriter, r *http.Request) {
    if r.Method != http.MethodPost {
        http.Error(w, "метод не поддерживается", http.StatusMethodNotAllowed)
        return
    }
    var user User
    if err := json.NewDecoder(r.Body).Decode(&user); err != nil {
        http.Error(w, "неверный JSON", http.StatusBadRequest)
        return
    }
    user.ID = 42
    w.WriteHeader(http.StatusCreated)
    json.NewEncoder(w).Encode(user)
}

func main() {
    mux := http.NewServeMux()
    mux.HandleFunc("/users", usersHandler)
    mux.HandleFunc("/users/create", createUserHandler)

    server := &http.Server{
        Addr:         ":8080",
        Handler:      mux,
        ReadTimeout:  5 * time.Second,
        WriteTimeout: 10 * time.Second,
    }

    fmt.Println("Сервер запущен на :8080")
    if err := server.ListenAndServe(); err != nil {
        fmt.Println("Ошибка:", err)
    }
}
```

**Теги JSON:** `json:"name"` — имя поля, `omitempty` — пропустить если пустое, `"-"` — никогда не сериализовывать.

**Задание:** добавь эндпоинт `GET /users/{id}` с возвратом пользователя по ID и ответом 404, если не найден.

---

## Модуль 12. Тестирование

```go
// math.go
package math

func Add(a, b int) int { return a + b }

func Fibonacci(n int) int {
    if n <= 1 {
        return n
    }
    return Fibonacci(n-1) + Fibonacci(n-2)
}
```

```go
// math_test.go
package math

import "testing"

func TestAdd(t *testing.T) {
    cases := []struct {
        a, b, want int
    }{
        {1, 2, 3},
        {0, 0, 0},
        {-1, 1, 0},
        {100, -50, 50},
    }
    for _, tc := range cases {
        got := Add(tc.a, tc.b)
        if got != tc.want {
            t.Errorf("Add(%d, %d) = %d, хотели %d", tc.a, tc.b, got, tc.want)
        }
    }
}

func BenchmarkFibonacci(b *testing.B) {
    for i := 0; i < b.N; i++ {
        Fibonacci(20)
    }
}
```

```bash
go test ./...          # запустить все тесты
go test -v ./...       # с выводом
go test -bench=.       # бенчмарки
go test -cover ./...   # покрытие
```

**Задание:** напиши тесты для `minMax` из модуля 4, включая edge cases: пустой срез, один элемент, все одинаковые.

---

## Финальный проект: CLI-утилита

Собери утилиту командной строки, которая:

- Принимает список URL как аргументы
- Делает HTTP-запросы параллельно (горутины + каналы)
- Выводит статус-код, время ответа и размер тела для каждого URL
- Имеет флаг `-timeout` для ограничения времени ожидания
- Покрыта тестами хотя бы на 60%

```bash
go run main.go -timeout=3s https://google.com https://github.com https://go.dev
```

Ожидаемый вывод:

```
https://google.com     200  142ms  14532 bytes
https://github.com     200  234ms  89210 bytes
https://go.dev         200  198ms  12043 bytes
```

---

## Что читать дальше

- [Официальный тур по Go](https://go.dev/tour/) — интерактивно прямо в браузере
- [Effective Go](https://go.dev/doc/effective_go) — официальный гайд по идиомам
- [Go by Example](https://gobyexample.com/) — справочник с примерами
- [100 Go Mistakes](https://100go.co/) — разбор типичных ошибок
- Стандартная библиотека: читай исходники `net/http`, `encoding/json`, `sync`

---

> Лучший способ выучить Go — писать на Go. Каждый модуль заканчивается заданием. Делай их.
