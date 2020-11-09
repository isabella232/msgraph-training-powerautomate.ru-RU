---
ms.openlocfilehash: 2d9b6e29a5ddc71b8f7b78b1e2fe035a8fdbddac
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829907"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="fdd18-101">В примере, созданном в предыдущем упражнении, используется `$batch` API для создания двух отдельных запросов к Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="fdd18-101">The Flow you created in the previous exercise uses the `$batch` API to make two individual requests to the Microsoft Graph.</span></span> <span data-ttu-id="fdd18-102">`$batch`Такой способ вызова конечной точки предоставляет некоторые преимущества и гибкость, но `$batch` при использовании нескольких запросов к Microsoft Graph в едином вызове возступает его работа `$batch` .</span><span class="sxs-lookup"><span data-stu-id="fdd18-102">Calling the `$batch` endpoint this way provides some benefit and flexibility, but the true power of the `$batch` endpoint comes when executing multiple requests to Microsoft Graph in a single `$batch` call.</span></span> <span data-ttu-id="fdd18-103">В этом упражнении вы узнаете, как создать единую группу и связать группу с созданием нескольких каналов по умолчанию для группы в едином `$batch` запросе.</span><span class="sxs-lookup"><span data-stu-id="fdd18-103">In this exercise, you will extend the example of creating a Unified Group and associating a Team to include creating multiple default Channels for the Team in a single `$batch` request.</span></span>

<span data-ttu-id="fdd18-104">Откройте [Microsoft Power автоматизирует](https://flow.microsoft.com) в браузере и войдите в систему с помощью учетной записи администратора клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="fdd18-104">Open [Microsoft Power Automate](https://flow.microsoft.com) in your browser and sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="fdd18-105">Выберите процесс, созданный на предыдущем шаге, и нажмите кнопку **изменить**.</span><span class="sxs-lookup"><span data-stu-id="fdd18-105">Select the Flow you created in the previous step and choose **Edit**.</span></span>

<span data-ttu-id="fdd18-106">Выберите **новый шаг** и введите `Batch` в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="fdd18-106">Choose **New step** and type `Batch` in the search box.</span></span> <span data-ttu-id="fdd18-107">Добавьте действие **пакетного соединителя MS Graph** .</span><span class="sxs-lookup"><span data-stu-id="fdd18-107">Add the **MS Graph Batch Connector** action.</span></span> <span data-ttu-id="fdd18-108">Нажмите кнопку с многоточием и переименуйте это действие в `Batch POST-channels` .</span><span class="sxs-lookup"><span data-stu-id="fdd18-108">Choose the ellipsis and rename this action to `Batch POST-channels`.</span></span>

<span data-ttu-id="fdd18-109">Добавьте следующий код в поле **основного** текста действия.</span><span class="sxs-lookup"><span data-stu-id="fdd18-109">Add the following code into the **body** text box of the action.</span></span>

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

<span data-ttu-id="fdd18-110">Обратите внимание, что в трех запросах выше используется свойство [dependsOn](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) для указания порядка следования, и каждый из них ВЫПОЛНЯЕТ запрос POST для создания нового канала в новой команде.</span><span class="sxs-lookup"><span data-stu-id="fdd18-110">Notice the three requests above are using the [dependsOn](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) property to specify a sequence order, and each will execute a POST request to create a new channel in the new Team.</span></span>

<span data-ttu-id="fdd18-111">Выберите каждый экземпляр `REPLACE` заполнителя, а затем в области динамический контент выберите **выражение** .</span><span class="sxs-lookup"><span data-stu-id="fdd18-111">Select each instance of the `REPLACE` placeholder, then select **Expression** in the dynamic content pane.</span></span> <span data-ttu-id="fdd18-112">Добавьте в **выражение** следующую формулу.</span><span class="sxs-lookup"><span data-stu-id="fdd18-112">Add the following formula into the **Expression**.</span></span>

```js
body('Batch_PUT-team').responses[0].body.id
```

![Снимок экрана с выражением в области динамического содержимого](./images/dynamic-expression.png)

<span data-ttu-id="fdd18-114">Нажмите кнопку **сохранить** , а затем выберите пункт **тест** для выполнения последовательности.</span><span class="sxs-lookup"><span data-stu-id="fdd18-114">Choose **Save** , then choose **Test** to execute the Flow.</span></span> <span data-ttu-id="fdd18-115">Установите переключатель действие **триггера** , а затем нажмите кнопку **сохранить & тест**.</span><span class="sxs-lookup"><span data-stu-id="fdd18-115">Select the **I'll perform the trigger** action radio button, then choose **Save & Test**.</span></span> <span data-ttu-id="fdd18-116">В поле **имя** введите уникальное имя группы без пробелов и нажмите кнопку **выполнить поток** для выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="fdd18-116">Enter a unique group name in the **Name** field without spaces, and choose **Run flow** to execute the Flow.</span></span>

<span data-ttu-id="fdd18-117">После запуска процесса нажмите кнопку Done ( **Готово** ), чтобы просмотреть журнал действий.</span><span class="sxs-lookup"><span data-stu-id="fdd18-117">Once the Flow starts, choose the **Done** button to see the activity log.</span></span> <span data-ttu-id="fdd18-118">По завершении потока итоговые выходные данные для `Batch POST-channels` действия будут иметь ответ о состоянии HTTP 201 для каждого созданного канала.</span><span class="sxs-lookup"><span data-stu-id="fdd18-118">When the Flow completes, the final output for the `Batch POST-channels` action has a 201 HTTP Status response for each Channel created.</span></span>

![Снимок журнала действий "успешный ход работы"](./images/batch-success.png)

<span data-ttu-id="fdd18-120">Перейдите в [Microsoft Teams](https://teams.microsoft.com) и войдите с помощью учетной записи администратора клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="fdd18-120">Browse to [Microsoft Teams](https://teams.microsoft.com) and sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="fdd18-121">Убедитесь, что отображается только что созданная команда и включает три канала, созданные `$batch` запросом.</span><span class="sxs-lookup"><span data-stu-id="fdd18-121">Verify that the team you just created appears and includes the three channels created by the `$batch` request.</span></span>

![Снимок экрана приложения Teams с новой командой и каналами, которые показаны](./images/team-channels.png)

<span data-ttu-id="fdd18-123">Хотя вышеприведенное `Batch POST-channels` действие было реализовано в этом руководстве как отдельное действие, вызовы для создания каналов могли быть добавлены в качестве дополнительных вызовов в `Batch PUT-team` действии.</span><span class="sxs-lookup"><span data-stu-id="fdd18-123">While the above `Batch POST-channels` action was implemented in this tutorial as a separate action, the calls to create the channels could have been added as additional calls in the `Batch PUT-team` action.</span></span> <span data-ttu-id="fdd18-124">Это приведет к созданию команды и всем каналам в едином пакетном звонке.</span><span class="sxs-lookup"><span data-stu-id="fdd18-124">This would have created the Team and all Channels in a single batch call.</span></span> <span data-ttu-id="fdd18-125">Попытайтесь сделать это самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="fdd18-125">Give that a try on your own.</span></span>

<span data-ttu-id="fdd18-126">Наконец, обратите внимание, что вызовы [пакетной обработки JSON](https://docs.microsoft.com/graph/json-batching) будут возвращать код состояния HTTP для каждого запроса.</span><span class="sxs-lookup"><span data-stu-id="fdd18-126">Finally, remember that [JSON Batching](https://docs.microsoft.com/graph/json-batching) calls will return an HTTP status code for each request.</span></span> <span data-ttu-id="fdd18-127">В рабочем процессе может потребоваться объединить обработку результатов с [`Apply to each`](https://docs.microsoft.com/power-automate/apply-to-each) действием и проверить, имеет ли каждый отдельный ответ код состояния 201, или компенсировать любые другие коды состояния.</span><span class="sxs-lookup"><span data-stu-id="fdd18-127">In a production process, you may want to combine post processing of the results with an [`Apply to each`](https://docs.microsoft.com/power-automate/apply-to-each) action and validate each individual response has a 201 status code or compensate for any other status codes received.</span></span>
