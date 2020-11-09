---
ms.openlocfilehash: 22c9c7ddd8513d857d96ade608e4b2e4e809dc41
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829887"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="fea5b-101">В этом упражнении вы создадите новое приложение Azure Active Directory, которое будет использоваться для предоставления делегированных разрешений для настраиваемого соединителя.</span><span class="sxs-lookup"><span data-stu-id="fea5b-101">In this exercise, you will create a new Azure Active Directory Application which will be used to provide the delegated permissions for the custom connector.</span></span>

<span data-ttu-id="fea5b-102">Откройте браузер и перейдите в [центр администрирования Azure Active Directory](https://aad.portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="fea5b-102">Open a browser and navigate to [Azure Active Directory admin center](https://aad.portal.azure.com).</span></span> <span data-ttu-id="fea5b-103">Выберите ссылку **Azure Active Directory** в левом меню навигации, а затем выберите запись **регистрации приложений** в разделе **Управление** в колонке **Azure Active Directory** .</span><span class="sxs-lookup"><span data-stu-id="fea5b-103">Choose the **Azure Active Directory** link in the left navigation menu, then choose the **App registrations** entry in the **Manage** section of the **Azure Active Directory** blade.</span></span>

![Снимок колонки Azure Active Directory в центре администрирования Azure Active Directory](./images/app-registrations.png)

<span data-ttu-id="fea5b-105">Выберите новый элемент меню **Регистрация** в верхней части колонки **Регистрация приложений** .</span><span class="sxs-lookup"><span data-stu-id="fea5b-105">Choose the **New registration** menu item at the top of the **App Registrations** blade.</span></span>

![Снимок колонки "Регистрация приложений" в центре администрирования Azure Active Directory](./images/new-registration.png)

<span data-ttu-id="fea5b-107">Введите `MS Graph Batch App` в поле **имя** .</span><span class="sxs-lookup"><span data-stu-id="fea5b-107">Enter `MS Graph Batch App` in the **Name** field.</span></span> <span data-ttu-id="fea5b-108">В разделе **Поддерживаемые типы учетных записей** выберите **учетные записи в любом организационном каталоге**.</span><span class="sxs-lookup"><span data-stu-id="fea5b-108">In the **Supported account types** section, select **Accounts in any organizational directory**.</span></span> <span data-ttu-id="fea5b-109">Оставьте незаполненным раздел **URI перенаправления** и выберите **регистр**.</span><span class="sxs-lookup"><span data-stu-id="fea5b-109">Leave the **Redirect URI** section blank and choose **Register**.</span></span>

![Снимок элемента регистрация в колонке приложения в центре администрирования Azure Active Directory](./images/register-an-app.png)

<span data-ttu-id="fea5b-111">В колонке **Пакетное приложение MS Graph** скопируйте **идентификатор Application (Client)**.</span><span class="sxs-lookup"><span data-stu-id="fea5b-111">On the **MS Graph Batch App** blade, copy the **Application (client) ID**.</span></span> <span data-ttu-id="fea5b-112">Это потребуется в следующем упражнении.</span><span class="sxs-lookup"><span data-stu-id="fea5b-112">You'll need this in the next exercise.</span></span>

![Снимок экрана со страницей "зарегистрированное приложение"](./images/app-id.png)

<span data-ttu-id="fea5b-114">Выберите элемент **разрешения API** в разделе **Управление** в колонке **пакетного приложения MS Graph** .</span><span class="sxs-lookup"><span data-stu-id="fea5b-114">Choose the **API permissions** entry in the **Manage** section of the **MS Graph Batch App** blade.</span></span> <span data-ttu-id="fea5b-115">Выберите **Добавить разрешение** в разделе **разрешения для API**.</span><span class="sxs-lookup"><span data-stu-id="fea5b-115">Choose **Add a permission** under **API permissions**.</span></span>

![Снимок колонки "разрешения API" на экране](./images/api-permissions.png)

<span data-ttu-id="fea5b-117">В колонке **запрос API разрешений** выберите **Microsoft Graph** , а затем — **делегированные разрешения**.</span><span class="sxs-lookup"><span data-stu-id="fea5b-117">In the **Request API permissions** blade, choose the **Microsoft Graph** , then choose **Delegated permissions**.</span></span> <span data-ttu-id="fea5b-118">Выполните поиск `group` , а затем выберите разрешение **чтение и запись всех групп** , делегированные разрешения.</span><span class="sxs-lookup"><span data-stu-id="fea5b-118">Search for `group`, then select the **Read and write all groups** delegated permission.</span></span> <span data-ttu-id="fea5b-119">В нижней части блейд-сайта выберите **Добавить разрешения** .</span><span class="sxs-lookup"><span data-stu-id="fea5b-119">Choose **Add permissions** at the bottom of the blade.</span></span>

 ![Снимок колонки с экраном разрешений API запроса](./images/select-permissions.png)

<span data-ttu-id="fea5b-121">Выберите " **Сертификаты и секреты** " в разделе **Управление** в колонке **пакетного приложения MS Graph** , а затем выберите **новый секрет клиента**.</span><span class="sxs-lookup"><span data-stu-id="fea5b-121">Choose the **Certificates and secrets** entry in the **Manage** section of the **MS Graph Batch App** blade, then choose **New client secret**.</span></span> <span data-ttu-id="fea5b-122">Введите `forever` в поле **Описание** и выберите пункт **никогда** в разделе **срок действия**.</span><span class="sxs-lookup"><span data-stu-id="fea5b-122">Enter `forever` in the **Description** and select **Never** under **Expires**.</span></span> <span data-ttu-id="fea5b-123">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="fea5b-123">Choose **Add**.</span></span>

![Снимок экрана сертификата и конфиденциальной колонки](./images/create-client-secret.png)

<span data-ttu-id="fea5b-125">Скопируйте значение для нового секрета.</span><span class="sxs-lookup"><span data-stu-id="fea5b-125">Copy the value for the new secret.</span></span> <span data-ttu-id="fea5b-126">Это потребуется в следующем упражнении.</span><span class="sxs-lookup"><span data-stu-id="fea5b-126">You'll need this in the next exercise.</span></span>

![Снимок экрана с новым секретом клиента](./images/copy-client-secret.png)

> [!IMPORTANT]
> <span data-ttu-id="fea5b-128">Этот шаг является критическим, так как секрет будет недоступен после закрытия этой колонки.</span><span class="sxs-lookup"><span data-stu-id="fea5b-128">This step is critical as the secret will not be accessible once you close this blade.</span></span> <span data-ttu-id="fea5b-129">Сохраните этот секрет в текстовом редакторе, чтобы использовать его в предстоящих упражнениях.</span><span class="sxs-lookup"><span data-stu-id="fea5b-129">Save this secret to a text editor for use in upcoming exercises.</span></span>

<span data-ttu-id="fea5b-130">Чтобы включить управление дополнительными службами через Microsoft Graph, в том числе свойства Teams, необходимо выбрать дополнительные, соответствующие области, чтобы разрешить управление определенными службами.</span><span class="sxs-lookup"><span data-stu-id="fea5b-130">To enable management of additional services accessible via the Microsoft Graph, including Teams properties, you would need to select additional, appropriate scopes to enable managing specific services.</span></span> <span data-ttu-id="fea5b-131">Например, чтобы расширить решение для создания записных книжек OneNote или планов планировщика, сегментов и задач, необходимо добавить необходимые области разрешений для соответствующих API.</span><span class="sxs-lookup"><span data-stu-id="fea5b-131">For example, to extend our solution to enable creating OneNote Notebooks or Planner plans, buckets and tasks you would need to add the required permission scopes for the relevant APIs.</span></span>
