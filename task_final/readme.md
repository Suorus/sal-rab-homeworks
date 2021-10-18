## Итоговое задание к блоку "Основы разработки"
Пишите код решения в файле `task_final/solution.js`

Автотесты запускаются в файле `task_final/test-runner.html`

#### Задача
Требуется исправить функцию для подготовки данных к отправке на сервер.

#### Ход решения
Исправьте функцию sendRequest.

Аргументы функции:
- имя клиента
- телефон клиента
- объект с адресом доставки: {street, house, entrance, floor, flat}
- список товаров в заказе
- стоимость заказа с учетом скидок и доставки

Как результат функции требуется вернуть JSON,
cформированный в соответствии с правилами.

Объект data должен содержать все данные.

В объекте data есть свойства:
- client - строка, имя клиента + телефон клиента;
- order - объект, содержащий данные о заказе:
    - address - строка с адресом доставки, записанным человекопонятным языком
    - sum - стоимость заказа с учетом скидок и доставки
- goods: массив объектов с информацией о позициях заказа:
    - title - название позиции
    - count - количество в заказе
    
например:

```json
{
  "data": {
    "client": "Иван +7(987)65-43-210",
    "order": {
      "address": "ул. Ленина, дом 1, 4 подъезд, 5 этаж, кв 53",
      "sum": 900
    },
    "goods": [
      {
        "title": "Пицца",
        "count": 2
      }
    ]
  }
}
```

### Как отправить решение на проверку
Проверьте перед отправкой решение с помощью автотеста.
Для проверки отправьте преподавателю на проверку ссылку на github
и ссылку на github-pages.

function sendRequest(name, phone, address, goods, sum) {
    let data = {goods: [], order: {}};

    let countOfGoods = goods.length;

    for (let i = 0; i <= countOfGoods; i += 1) {
        data.goods.push(goods[i].title);
    }

    data.order.address = address;
    data.order.sum = name + phone + address + goods + sum;

    data.client = 'Иван';

    let jsonData = JSON.stringify(data);

    return jsonData;
}

function sendRequest(name, phone, address, goods, sum) {
    let data = {order: {}, goods: []};

    let countOfGoods = goods.length;

    for (let i = 0; i < countOfGoods; i += 1 ) {
        data.goods.push ({title: goods[i].title, count: goods[i].count});
    }
   
    data.order.address = "ул. " + address.street + ", дом " + address.house + ", " +address.entrance + " подъезд, " + address.floor + " этаж, кв " + address.flat;
    data.order.sum = sum;

    data.client = name + " " + phone;

    let jsonData = JSON.stringify({data});

    return jsonData;
}

function sendRequest(name, phone, address, goods, sum) {
    let data = {client: {name, phone},order: {address, sum}, goods: [{title, count}]};
    let countOfGoods = goods.length;

    for (let i = 0; i <= countOfGoods; i += 1) {
        data.goods.push(goods[i].title);
    }

    data.order.address = address;
    data.order.sum = name + phone + address + goods + sum;

    data.client = 'Иван';

    let jsonData = JSON.stringify({data});

    return jsonData;
}

function sendRequest(name, phone, address, goods, sum) {
    let data = {client: "", order: {}, goods: []};

    let countOfGoods = goods.length;

    for (let i = 0; i <= countOfGoods-1; i += 1) {
        data.goods.push({title: goods[i].title, count: goods[i].count});
    }

    data.order.address = `ул. ${address.street}, дом ${address.house}, ${address.entrance} подъезд, ${address.floor} этаж, кв ${address.flat}`;
    data.order.sum = sum;

    data.client = `${name} ${phone}`;
    
    let jsonData = JSON.stringify({data});
    return jsonData;
}