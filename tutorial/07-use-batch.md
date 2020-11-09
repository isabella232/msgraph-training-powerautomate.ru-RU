---
ms.openlocfilehash: 2d9b6e29a5ddc71b8f7b78b1e2fe035a8fdbddac
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829907"
---
<!-- markdownlint-disable MD002 MD041 -->

В примере, созданном в предыдущем упражнении, используется `$batch` API для создания двух отдельных запросов к Microsoft Graph. `$batch`Такой способ вызова конечной точки предоставляет некоторые преимущества и гибкость, но `$batch` при использовании нескольких запросов к Microsoft Graph в едином вызове возступает его работа `$batch` . В этом упражнении вы узнаете, как создать единую группу и связать группу с созданием нескольких каналов по умолчанию для группы в едином `$batch` запросе.

Откройте [Microsoft Power автоматизирует](https://flow.microsoft.com) в браузере и войдите в систему с помощью учетной записи администратора клиента Office 365. Выберите процесс, созданный на предыдущем шаге, и нажмите кнопку **изменить**.

Выберите **новый шаг** и введите `Batch` в поле поиска. Добавьте действие **пакетного соединителя MS Graph** . Нажмите кнопку с многоточием и переименуйте это действие в `Batch POST-channels` .

Добавьте следующий код в поле **основного** текста действия.

```json
{
  "requests": [
    {
      "id": 1,
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Marketing Collateral",
        "description": "Marketing collateral and documentation."
      }
    },
    {
      "id": 2,
      "dependsOn": [
        "1"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Vendor Contracts",
        "description": "Vendor documents, contracts, agreements and schedules."
      }
    },
    {
      "id": 3,
      "dependsOn": [
        "2"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "General Client Agreements",
        "description": "General Client documents and agreements."
      }
    }
  ]
}
```

Обратите внимание, что в трех запросах выше используется свойство [dependsOn](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) для указания порядка следования, и каждый из них ВЫПОЛНЯЕТ запрос POST для создания нового канала в новой команде.

Выберите каждый экземпляр `REPLACE` заполнителя, а затем в области динамический контент выберите **выражение** . Добавьте в **выражение** следующую формулу.

```js
body('Batch_PUT-team').responses[0].body.id
```

![Снимок экрана с выражением в области динамического содержимого](./images/dynamic-expression.png)

Нажмите кнопку **сохранить** , а затем выберите пункт **тест** для выполнения последовательности. Установите переключатель действие **триггера** , а затем нажмите кнопку **сохранить & тест**. В поле **имя** введите уникальное имя группы без пробелов и нажмите кнопку **выполнить поток** для выполнения потока.

После запуска процесса нажмите кнопку Done ( **Готово** ), чтобы просмотреть журнал действий. По завершении потока итоговые выходные данные для `Batch POST-channels` действия будут иметь ответ о состоянии HTTP 201 для каждого созданного канала.

![Снимок журнала действий "успешный ход работы"](./images/batch-success.png)

Перейдите в [Microsoft Teams](https://teams.microsoft.com) и войдите с помощью учетной записи администратора клиента Office 365. Убедитесь, что отображается только что созданная команда и включает три канала, созданные `$batch` запросом.

![Снимок экрана приложения Teams с новой командой и каналами, которые показаны](./images/team-channels.png)

Хотя вышеприведенное `Batch POST-channels` действие было реализовано в этом руководстве как отдельное действие, вызовы для создания каналов могли быть добавлены в качестве дополнительных вызовов в `Batch PUT-team` действии. Это приведет к созданию команды и всем каналам в едином пакетном звонке. Попытайтесь сделать это самостоятельно.

Наконец, обратите внимание, что вызовы [пакетной обработки JSON](https://docs.microsoft.com/graph/json-batching) будут возвращать код состояния HTTP для каждого запроса. В рабочем процессе может потребоваться объединить обработку результатов с [`Apply to each`](https://docs.microsoft.com/power-automate/apply-to-each) действием и проверить, имеет ли каждый отдельный ответ код состояния 201, или компенсировать любые другие коды состояния.
