---
ms.openlocfilehash: bf83723de025f3e1f6bde5b4226fc8966dff6b9a
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829734"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="47e46-101">Последняя настройка, позволяющая убедиться, что соединитель готов к использованию, — авторизация и тестирование настраиваемого соединителя для создания кэшированного подключения.</span><span class="sxs-lookup"><span data-stu-id="47e46-101">The final configuration step to ensure the connector is ready for use is to authorize and test the custom connector to create a cached connection.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47e46-102">Для выполнения описанных ниже действий необходимо войти в систему с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="47e46-102">The following steps requires that you are logged in with administrator privileges.</span></span>

<span data-ttu-id="47e46-103">В [Microsoft Power Автоматизация](https://flow.microsoft.com)перейдите к пункту меню **данные** слева и выберите страницу **подключения** .</span><span class="sxs-lookup"><span data-stu-id="47e46-103">In [Microsoft Power Automate](https://flow.microsoft.com), go to the **Data** menu item on the left and choose the **Connections** page.</span></span> <span data-ttu-id="47e46-104">Выберите ссылку **создать подключение** .</span><span class="sxs-lookup"><span data-stu-id="47e46-104">Choose the **New Connection** link.</span></span>

![Снимок экрана с кнопкой "создать подключение"](./images/new-connection.png)

<span data-ttu-id="47e46-106">Найдите свой настраиваемый соединитель и завершите подключение, нажав кнопку со знаком "плюс".</span><span class="sxs-lookup"><span data-stu-id="47e46-106">Find your custom connector and complete the connection by clicking the plus button.</span></span> <span data-ttu-id="47e46-107">Войдите с помощью учетной записи Azure Active Directory администратора клиента Office 365.</span><span class="sxs-lookup"><span data-stu-id="47e46-107">Sign in with your Office 365 tenant administrator's Azure Active Directory account.</span></span>

![Снимок экрана со списком подключений](./images/connection-sign-in.png)

<span data-ttu-id="47e46-109">При получении запроса на получение запрошенных разрешений проверяйте **согласие от имени вашей организации** , а затем нажмите кнопку **принять** для авторизации разрешений.</span><span class="sxs-lookup"><span data-stu-id="47e46-109">When prompted for the requested permissions, check **Consent on behalf of your organization** and then choose **Accept** to authorize permissions.</span></span>

![Снимок экрана с запросом согласия](./images/consent-prompt.png)

<span data-ttu-id="47e46-111">После авторизации разрешений подключение будет создано в Power Автоматизация.</span><span class="sxs-lookup"><span data-stu-id="47e46-111">After you authorize the permissions, a connection is created in Power Automate.</span></span>

<span data-ttu-id="47e46-112">Настраиваемый соединитель теперь настроен и включен.</span><span class="sxs-lookup"><span data-stu-id="47e46-112">The custom connector is now configured and enabled.</span></span> <span data-ttu-id="47e46-113">Возможна задержка, связанная с применением и доступностью разрешений, но соединитель настроен.</span><span class="sxs-lookup"><span data-stu-id="47e46-113">There may be a delay in permissions being applied and available, but the connector is now configured.</span></span>
