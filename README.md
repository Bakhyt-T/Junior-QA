# Junior-QA
Тестовые задания для Junior QA
### 1. Задача по написанию тест-кейсов
#### Позитивные:
##### 1. Проверка отображения всех элементов списка
Убедиться, что все страны и их коды отображаются корректно.
##### Шаги:
1. Открыть страницу с выпадающим списком.
2. Нажать на стрелку для раскрытия списка.
3. Визуально проверить, что все ожидаемые страны присутствуют.
4. Сравнить отображаемые коды с официальными данными.
##### Ожидаемый результат: 
Все страны и их коды отображаются полностью и правильно.
##### 2. Выбор каждой страны из списка и проверка соответствию кода
Проверить, что при выборе страны автоматически заполняется правильный телефонный код.
##### Шаги:
1. Открыть список.
2. Выбрать страну.
3. Проверить, что поле с кодом телефона содержит правильное значение.
##### Ожидаемый результат:
После выбора страны в поле с кодом телефона отображается правильный код.
##### 3. Проверка автоматического заполнения кода при вводе названия страны
Убедиться, что при вводе названия страны или его части происходит автоматическая синхронизация.
##### Шаги:
1. Ввести название страны в поле поиска или в поле выбора.
2. Наблюдать за автоматическим заполнением поля с кодом телефона.
##### Ожидаемый результат:
Поле с кодом заполняется правильным значением.
##### 4. Проверка поиска по списку (если реализован)
Убедиться, что поиск работает корректно и фильтрует список.
##### Шаги:
1. Ввести часть названия страны в поле поиска.
2. Выбрать найденную страну.
3. Проверить правильность выбранной страны и кода.
##### Ожидаемый результат:
В списке отображаются только подходящие по поисковому запросу страны. После выбора отображается правильный телефонный код.

#### Негативные:
##### 1. Попытка выбрать страну, которой нет в списке (ввод вручную)
Проверить реакцию системы на некорректный ввод вручную.
##### Шаги:
1. Ввести название отсутствующей в списке страны вручную в поле выбора.
2. Попытаться подтвердить выбор или оставить поле пустым.
##### Ожидаемый результат:
Ввод либо игнорируется, либо появляется сообщение об ошибке. Не допускается выбор недопустимой страны.
##### 2. Ввод некорректных данных (опечатки или неправильный формат)
Проверить устойчивость системы к ошибкам ввода.
##### Шаги:
1. Ввести неправильное название страны (например, "Москва" вместо "Россия").
2. Попытаться выбрать или подтвердить ввод.
##### Ожидаемый результат:
Система не выбирает страну или показывает сообщение о некорректном вводе.
##### 3. Оставление поля без выбора и попытка отправки формы
Проверить обязательность выбора страны перед отправкой формы.
##### Шаги:
1. Оставить список без выбора.
2. Нажать кнопку "Отправить" или "Ввод".
##### Ожидаемый результат:
Появляется сообщение о необходимости выбрать страну или выделяется обязательное поле.
##### 4. Проверка реакции на быстрое повторное изменение выбора
Убедиться, что система стабильно обрабатывает быстрые изменения.
##### Шаги:
1. Быстро несколько раз менять выбранную страну.
2. Обратить внимание на возможные зависания или ошибки интерфейса.
##### Ожидаемый результат:
Интерфейс корректно обновляется без ошибок или зависаний.
##### 5. Проверка наличия ошибок при отсутствии данных о стране/коде
Обеспечить обработку случаев отсутствия данных о стране или её коде в базе данных/списке.
##### Шаги:
1. Искусственно удалить данные о какой-либо стране из списка (если есть возможность).
2. Попробовать выбрать эту страну или проверить её наличие в списке.
##### Ожидаемый результат:
Страна отсутствует в списке или появляется сообщение об ошибке/отсутствии данных.

### 2. Задача Playwright
// tests/title.spec.js
const { test, expect } = require('@playwright/test');

test.describe('Проверка заголовка страницы https://playwright.dev/', () => {
  // Тест для Chromium
  test('Проверка заголовка в Chromium', async ({ page }) => {
    await page.goto('https://playwright.dev/');
    await expect(page).toHaveTitle(/Playwright/);
  });

  // Тест для Firefox
  test('Проверка заголовка в Firefox', async ({ browserName }) => {
    const { chromium, firefox } = require('@playwright/test');
    const browserType = browserName === 'firefox' ? firefox : chromium;
    const browser = await browserType.launch();
    const context = await browser.newContext();
    const page = await context.newPage();

    await page.goto('https://playwright.dev/');
    await expect(page).toHaveTitle(/Playwright/);

    await browser.close();
  });
});

1. Тест открывает страницу https://playwright.dev/.
2. Проверяет, что заголовок содержит слово "Playwright".
3. Запускается минимум на двух браузерах (Chromium и Firefox).

### 3. Задача по теории вероятности:
Дано:
Красных шаров: 7;
Зеленых шаров: 5;
Синих шаров: 8;
Общее количество шаров:7+5+8=20.
##### Решение:
Вероятность того, что шар будет красным или зеленым, равна сумме вероятностей выбрать красный или зеленый шар. 7/20 + 5/20 = 12/20 = 3/5 или 0,6 или 60%
