---
ms.openlocfilehash: 90462157024c529a1cf183230298fbf80813b8c9
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829898"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="7f835-101">В этом упражнении вы создадите новый настраиваемый соединитель, который можно использовать в Microsoft Power автоматизиру или в логических приложениях Azure.</span><span class="sxs-lookup"><span data-stu-id="7f835-101">In this exercise, you will create a new custom connector which can be used in Microsoft Power Automate or in Azure Logic Apps.</span></span> <span data-ttu-id="7f835-102">В файле определения Опенапи предварительно создается правильный путь к `$batch` конечной точке Microsoft Graph и дополнительные параметры для включения простого импорта.</span><span class="sxs-lookup"><span data-stu-id="7f835-102">The OpenAPI definition file is prebuilt with the correct path for the Microsoft Graph `$batch` endpoint and additional settings to enable simple import.</span></span>

<span data-ttu-id="7f835-103">Существует два способа создания настраиваемого соединителя для Microsoft Graph:</span><span class="sxs-lookup"><span data-stu-id="7f835-103">There are two options to create a custom connector for Microsoft Graph:</span></span>

- <span data-ttu-id="7f835-104">Создать из пустого</span><span class="sxs-lookup"><span data-stu-id="7f835-104">Create from blank</span></span>
- <span data-ttu-id="7f835-105">Импорт файла Опенапи</span><span class="sxs-lookup"><span data-stu-id="7f835-105">Import an OpenAPI file</span></span>

## <a name="option-1-create-custom-connector-from-blank-template"></a><span data-ttu-id="7f835-106">Вариант 1: Создание настраиваемого соединителя из пустого шаблона</span><span class="sxs-lookup"><span data-stu-id="7f835-106">Option 1: Create custom connector from blank template</span></span>

<span data-ttu-id="7f835-107">Откройте браузер и перейдите в раздел [Автоматизация управления питанием (Майкрософт](https://flow.microsoft.com)).</span><span class="sxs-lookup"><span data-stu-id="7f835-107">Open a browser and navigate to [Microsoft Power Automate](https://flow.microsoft.com).</span></span> <span data-ttu-id="7f835-108">Войдите с помощью учетной записи администратора клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="7f835-108">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="7f835-109">Выберите **данные** в левой части меню, а затем выберите элемент **настраиваемые соединители** в раскрывающемся меню.</span><span class="sxs-lookup"><span data-stu-id="7f835-109">Choose **Data** on the left-hand side menu, and select the **Custom Connectors** item in the drop-down menu.</span></span>

![Снимок экрана с раскрывающимся меню в Microsoft Power автоматизиру](./images/custom-connectors.png)

<span data-ttu-id="7f835-111">На странице " **настраиваемые соединители** " выберите ссылку **создать настраиваемый соединитель** в правом верхнем углу, а затем в раскрывающемся меню выберите **создать из пустого** элемента.</span><span class="sxs-lookup"><span data-stu-id="7f835-111">On the **Custom Connectors** page choose the **New custom connector** link in the top right, then select the **Create from blank** item in the drop-down menu.</span></span>

![Снимок экрана с раскрывающимся меню нового пользовательского соединителя в Microsoft Power автоматизиру](./images/new-connector.png)

<span data-ttu-id="7f835-113">Введите `MS Graph Batch Connector` в текстовом поле **имя соединителя** .</span><span class="sxs-lookup"><span data-stu-id="7f835-113">Enter `MS Graph Batch Connector` in the **Connector name** text box.</span></span> <span data-ttu-id="7f835-114">Choose **Continue**.</span><span class="sxs-lookup"><span data-stu-id="7f835-114">Choose **Continue**.</span></span>

<span data-ttu-id="7f835-115">На странице Настройка соединителя ( **Общие** ) заполните поля, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="7f835-115">On the connector configuration **General** page, fill in the fields as follows.</span></span>

- <span data-ttu-id="7f835-116">**Схема** : HTTPS</span><span class="sxs-lookup"><span data-stu-id="7f835-116">**Scheme** : HTTPS</span></span>
- <span data-ttu-id="7f835-117">**Узел** : `graph.microsoft.com`</span><span class="sxs-lookup"><span data-stu-id="7f835-117">**Host** : `graph.microsoft.com`</span></span>
- <span data-ttu-id="7f835-118">**Базовый URL-адрес** : `/`</span><span class="sxs-lookup"><span data-stu-id="7f835-118">**Base URL** : `/`</span></span>

<span data-ttu-id="7f835-119">Нажмите кнопку **Безопасность** , чтобы продолжить.</span><span class="sxs-lookup"><span data-stu-id="7f835-119">Choose **Security** button to continue.</span></span>

![Снимок экрана вкладки "Общие" в конфигурации соединителя](./images/general-tab.png)

<span data-ttu-id="7f835-121">На странице **Безопасность** заполните поля, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="7f835-121">On the **Security** page, fill in the fields as follows.</span></span>

- <span data-ttu-id="7f835-122">**Выберите, какую проверку подлинности реализует ваш API** : `OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="7f835-122">**Choose what authentication is implemented by your API** : `OAuth 2.0`</span></span>
- <span data-ttu-id="7f835-123">**Поставщик удостоверений** : `Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="7f835-123">**Identity Provider** : `Azure Active Directory`</span></span>
- <span data-ttu-id="7f835-124">**Идентификатор клиента** : идентификатор приложения, созданный в предыдущем упражнении</span><span class="sxs-lookup"><span data-stu-id="7f835-124">**Client id** : the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="7f835-125">**Секрет клиента** : ключ, созданный в предыдущем упражнении</span><span class="sxs-lookup"><span data-stu-id="7f835-125">**Client secret** : the key you created in the previous exercise</span></span>
- <span data-ttu-id="7f835-126">**URL-адрес входа** : `https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="7f835-126">**Login url** : `https://login.windows.net`</span></span>
- <span data-ttu-id="7f835-127">**Идентификатор клиента** : `common`</span><span class="sxs-lookup"><span data-stu-id="7f835-127">**Tenant ID** : `common`</span></span>
- <span data-ttu-id="7f835-128">**URL-адрес ресурса** : `https://graph.microsoft.com` (без замыкающего/)</span><span class="sxs-lookup"><span data-stu-id="7f835-128">**Resource URL** : `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="7f835-129">**Область** : оставьте пустым</span><span class="sxs-lookup"><span data-stu-id="7f835-129">**Scope** : Leave blank</span></span>

<span data-ttu-id="7f835-130">Нажмите кнопку **определения** , чтобы продолжить.</span><span class="sxs-lookup"><span data-stu-id="7f835-130">Choose **Definition** button to continue.</span></span>

![Снимок экрана вкладки "безопасность" в конфигурации соединителя](./images/security-tab.png)

<span data-ttu-id="7f835-132">На странице **Определение** выберите **создать действие** и заполните поля, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="7f835-132">On the **Definition** page, select **New Action** and fill in the fields as follows.</span></span>

- <span data-ttu-id="7f835-133">**Сводка** : `Batch`</span><span class="sxs-lookup"><span data-stu-id="7f835-133">**Summary** : `Batch`</span></span>
- <span data-ttu-id="7f835-134">**Description** : `Execute Batch with Delegate Permission`</span><span class="sxs-lookup"><span data-stu-id="7f835-134">**Description** : `Execute Batch with Delegate Permission`</span></span>
- <span data-ttu-id="7f835-135">**Идентификатор операции** : `Batch`</span><span class="sxs-lookup"><span data-stu-id="7f835-135">**Operation ID** : `Batch`</span></span>
- <span data-ttu-id="7f835-136">**Видимость** : `important`</span><span class="sxs-lookup"><span data-stu-id="7f835-136">**Visibility** : `important`</span></span>

![Снимок экрана вкладки определения в конфигурации соединителя](./images/definition-tab.png)

<span data-ttu-id="7f835-138">Создайте **запрос** , выбрав пункт **Импорт из примера** и заполните поля, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="7f835-138">Create **Request** by selecting **Import from Sample** and fill in the fields as follows.</span></span>

- <span data-ttu-id="7f835-139">**Команда** : `POST`</span><span class="sxs-lookup"><span data-stu-id="7f835-139">**Verb** : `POST`</span></span>
- <span data-ttu-id="7f835-140">**URL-адрес** : `https://graph.microsoft.com/v1.0/$batch`</span><span class="sxs-lookup"><span data-stu-id="7f835-140">**URL** : `https://graph.microsoft.com/v1.0/$batch`</span></span>
- <span data-ttu-id="7f835-141">**Заголовки** : оставьте пустым</span><span class="sxs-lookup"><span data-stu-id="7f835-141">**Headers** : Leave blank</span></span>
- <span data-ttu-id="7f835-142">**Основной текст** : `{}`</span><span class="sxs-lookup"><span data-stu-id="7f835-142">**Body** : `{}`</span></span>

<span data-ttu-id="7f835-143">Нажмите кнопку **Импорт**.</span><span class="sxs-lookup"><span data-stu-id="7f835-143">Select **Import**.</span></span>

![Снимок экрана с примером диалогового окна "Импорт из" в конфигурации соединителя](./images/import-sample.png)

<span data-ttu-id="7f835-145">Выберите **создать соединитель** в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="7f835-145">Choose **Create Connector** on the top-right.</span></span> <span data-ttu-id="7f835-146">После создания соединителя Скопируйте созданный **URL-адрес перенаправления** с страницы " **Безопасность** ".</span><span class="sxs-lookup"><span data-stu-id="7f835-146">After the connector has been created, copy the generated **Redirect URL** from **Security** page.</span></span>

![Снимок экрана с созданным URL-адресом перенаправления](./images/redirect-url.png)

<span data-ttu-id="7f835-148">Вернитесь к зарегистрированному приложению на [портале Azure](https://aad.portal.azure.com) , созданному в предыдущем упражнении.</span><span class="sxs-lookup"><span data-stu-id="7f835-148">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="7f835-149">Выберите пункт **Проверка подлинности** в левой части меню.</span><span class="sxs-lookup"><span data-stu-id="7f835-149">Select **Authentication** on the left-hand side menu.</span></span> <span data-ttu-id="7f835-150">Нажмите кнопку **Добавить платформу** , а затем выберите пункт **веб**.</span><span class="sxs-lookup"><span data-stu-id="7f835-150">Select **Add a platform** , then select **Web**.</span></span> <span data-ttu-id="7f835-151">Введите URL-адрес перенаправления, скопированный на предыдущем шаге в **URI перенаправления** , а затем нажмите кнопку **настроить**.</span><span class="sxs-lookup"><span data-stu-id="7f835-151">Enter the redirect URL copied from the previous step in the **Redirect URIs** , then select **Configure**.</span></span>

![Снимок колонки "URL-адреса ответа" на портале Azure](./images/update-app-reg.png)

## <a name="option-2-create-custom-connector-by-importing-openapi-file"></a><span data-ttu-id="7f835-153">Вариант 2: Создание настраиваемого соединителя путем импорта файла Опенапи</span><span class="sxs-lookup"><span data-stu-id="7f835-153">Option 2: Create custom connector by importing OpenAPI file</span></span>

<span data-ttu-id="7f835-154">С помощью текстового редактора создайте новый пустой файл с именем `MSGraph-Delegate-Batch.swagger.json` и добавьте приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="7f835-154">Using a text editor, create a new empty file named `MSGraph-Delegate-Batch.swagger.json` and add the following code.</span></span>

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

<span data-ttu-id="7f835-155">Откройте браузер и перейдите в раздел [Автоматизация управления питанием (Майкрософт](https://flow.microsoft.com)).</span><span class="sxs-lookup"><span data-stu-id="7f835-155">Open a browser and navigate to [Microsoft Power Automate](https://flow.microsoft.com).</span></span> <span data-ttu-id="7f835-156">Войдите с помощью учетной записи администратора клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="7f835-156">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="7f835-157">Выберите **данные** в левой части меню, а затем выберите элемент **настраиваемые соединители** в раскрывающемся меню.</span><span class="sxs-lookup"><span data-stu-id="7f835-157">Choose **Data** on the left-hand side menu, and select the **Custom Connectors** item in the drop-down menu.</span></span>

<span data-ttu-id="7f835-158">На странице " **настраиваемые соединители** " выберите ссылку **создать настраиваемый соединитель** в правом верхнем углу, а затем в раскрывающемся меню выберите пункт **импортировать файл опенапи** .</span><span class="sxs-lookup"><span data-stu-id="7f835-158">On the **Custom Connectors** page choose the **New custom connector** link in the top right, then select the **Import an OpenAPI file** item in the drop-down menu.</span></span>

<span data-ttu-id="7f835-159">Введите `MS Graph Batch Connector` в текстовом поле **имя соединителя** .</span><span class="sxs-lookup"><span data-stu-id="7f835-159">Enter `MS Graph Batch Connector` in the **Connector name** text box.</span></span> <span data-ttu-id="7f835-160">Щелкните значок папки, чтобы отправить файл Опенапи.</span><span class="sxs-lookup"><span data-stu-id="7f835-160">Choose the folder icon to upload the OpenAPI file.</span></span> <span data-ttu-id="7f835-161">Перейдите к `MSGraph-Delegate-Batch.swagger.json` созданному файлу.</span><span class="sxs-lookup"><span data-stu-id="7f835-161">Browse to the `MSGraph-Delegate-Batch.swagger.json` file you created.</span></span> <span data-ttu-id="7f835-162">Нажмите **продолжить** , чтобы отправить файл опенапи.</span><span class="sxs-lookup"><span data-stu-id="7f835-162">Choose **Continue** to upload the OpenAPI file.</span></span>

<span data-ttu-id="7f835-163">На странице Конфигурация соединителя выберите ссылку **Безопасность** в меню Навигация.</span><span class="sxs-lookup"><span data-stu-id="7f835-163">On the connector configuration page, choose the **Security** link in the navigation menu.</span></span> <span data-ttu-id="7f835-164">Заполните поля, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="7f835-164">Fill in the fields as follows.</span></span>

- <span data-ttu-id="7f835-165">**Выберите, какую проверку подлинности реализует ваш API** : `OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="7f835-165">**Choose what authentication is implemented by your API** : `OAuth 2.0`</span></span>
- <span data-ttu-id="7f835-166">**Поставщик удостоверений** : `Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="7f835-166">**Identity Provider** : `Azure Active Directory`</span></span>
- <span data-ttu-id="7f835-167">**Идентификатор клиента** : идентификатор приложения, созданный в предыдущем упражнении</span><span class="sxs-lookup"><span data-stu-id="7f835-167">**Client id** : the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="7f835-168">**Секрет клиента** : ключ, созданный в предыдущем упражнении</span><span class="sxs-lookup"><span data-stu-id="7f835-168">**Client secret** : the key you created in the previous exercise</span></span>
- <span data-ttu-id="7f835-169">**URL-адрес входа** : `https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="7f835-169">**Login url** : `https://login.windows.net`</span></span>
- <span data-ttu-id="7f835-170">**Идентификатор клиента** : `common`</span><span class="sxs-lookup"><span data-stu-id="7f835-170">**Tenant ID** : `common`</span></span>
- <span data-ttu-id="7f835-171">**URL-адрес ресурса** : `https://graph.microsoft.com` (без замыкающего/)</span><span class="sxs-lookup"><span data-stu-id="7f835-171">**Resource URL** : `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="7f835-172">**Область** : оставьте пустым</span><span class="sxs-lookup"><span data-stu-id="7f835-172">**Scope** : Leave blank</span></span>

<span data-ttu-id="7f835-173">Выберите **создать соединитель** в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="7f835-173">Choose **Create Connector** on the top-right.</span></span> <span data-ttu-id="7f835-174">После создания соединителя Скопируйте созданный **URL-адрес перенаправления**.</span><span class="sxs-lookup"><span data-stu-id="7f835-174">After the connector has been created, copy the generated **Redirect URL**.</span></span>

![Снимок экрана с созданным URL-адресом перенаправления](./images/redirect-url.png)

<span data-ttu-id="7f835-176">Вернитесь к зарегистрированному приложению на [портале Azure](https://aad.portal.azure.com) , созданному в предыдущем упражнении.</span><span class="sxs-lookup"><span data-stu-id="7f835-176">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="7f835-177">Выберите пункт **Проверка подлинности** в левой части меню.</span><span class="sxs-lookup"><span data-stu-id="7f835-177">Select **Authentication** on the left-hand side menu.</span></span> <span data-ttu-id="7f835-178">Нажмите кнопку **Добавить платформу** , а затем выберите пункт **веб**.</span><span class="sxs-lookup"><span data-stu-id="7f835-178">Select **Add a platform** , then select **Web**.</span></span> <span data-ttu-id="7f835-179">Введите URL-адрес перенаправления, скопированный на предыдущем шаге в **URI перенаправления** , а затем нажмите кнопку **настроить**.</span><span class="sxs-lookup"><span data-stu-id="7f835-179">Enter the redirect URL copied from the previous step in the **Redirect URIs** , then select **Configure**.</span></span>

![Снимок колонки "URL-адреса ответа" на портале Azure](./images/update-app-reg.png)
