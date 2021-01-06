---
title: Configurer un serveur proxy lors de l’utilisation du kit de développement logiciel (SDK) Azure pour .NET
description: Utiliser HTTP [S] _PROXY des variables d’environnement pour définir un proxy pour le kit de développement logiciel (SDK) Azure pour .NET
ms.date: 12/10/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.openlocfilehash: 64d525f8a6c277a5ac383dfded828f2fd3cfd744
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701121"
---
# <a name="configure-a-proxy-server-when-using-the-azure-sdk-for-net"></a><span data-ttu-id="3b48d-103">Configurer un serveur proxy lors de l’utilisation du kit de développement logiciel (SDK) Azure pour .NET</span><span class="sxs-lookup"><span data-stu-id="3b48d-103">Configure a proxy server when using the Azure SDK for .NET</span></span>

<span data-ttu-id="3b48d-104">Si votre organisation requiert l’utilisation d’un serveur proxy pour accéder aux ressources Internet, vous devez définir une variable d’environnement avec les informations du serveur proxy pour utiliser le kit de développement logiciel (SDK) Azure pour .NET.</span><span class="sxs-lookup"><span data-stu-id="3b48d-104">If your organization requires the use of a proxy server to access internet resources, you will need to set an environment variable with the proxy server information to use the Azure SDK for .NET.</span></span>  

## <a name="configuration-using-environment-variables"></a><span data-ttu-id="3b48d-105">Configuration à l’aide de variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="3b48d-105">Configuration using environment variables</span></span>

<span data-ttu-id="3b48d-106">Selon que votre serveur proxy utilise le protocole HTTP ou HTTPs, vous devez définir la variable d’environnement `HTTP_PROXY` ou, `HTTPS_PROXY` respectivement.</span><span class="sxs-lookup"><span data-stu-id="3b48d-106">Depending on if your proxy server uses HTTP or HTTPS, you will set either the environment variable `HTTP_PROXY` or `HTTPS_PROXY` respectively.</span></span> <span data-ttu-id="3b48d-107">L’URL du serveur proxy se présente sous la forme `http[s]://[username:password@]<ip_address_or_hostname>:<port>/` dans laquelle la `username:password` combinaison est facultative.</span><span class="sxs-lookup"><span data-stu-id="3b48d-107">The proxy server URL has the form `http[s]://[username:password@]<ip_address_or_hostname>:<port>/` where the `username:password` combination is optional.</span></span> <span data-ttu-id="3b48d-108">Pour obtenir l’adresse IP ou le nom d’hôte, le port et les informations d’identification de votre serveur proxy, consultez votre administrateur réseau.</span><span class="sxs-lookup"><span data-stu-id="3b48d-108">To get the IP address or hostname, port and credentials for your proxy server, consult your network administrator.</span></span>

<span data-ttu-id="3b48d-109">Les exemples suivants montrent comment définir les variables d’environnement appropriées dans les environnements de l’interface de commande (Windows) et bash (Linux/Mac).</span><span class="sxs-lookup"><span data-stu-id="3b48d-109">The following examples show how to set the appropriate environment variables in command shell (Windows) and bash (Linux/Mac) environments.</span></span>  <span data-ttu-id="3b48d-110">En définissant la variable d’environnement appropriée, le kit de développement logiciel (SDK) Azure pour .NET utilise le serveur proxy lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3b48d-110">Setting the appropriate environment variable will then cause the Azure SDK for .NET to use the proxy server at runtime.</span></span>

### <a name="cmd"></a>[<span data-ttu-id="3b48d-111">cmd</span><span class="sxs-lookup"><span data-stu-id="3b48d-111">cmd</span></span>](#tab/cmd)

```cmd
rem Non-authenticated HTTP server:
set HTTP_PROXY=http://10.10.1.10:1180

rem Authenticated HTTP server:
set HTTP_PROXY=http://username:password@10.10.1.10:1180

rem Non-authenticated HTTPS server:
set HTTPS_PROXY=http://10.10.1.10:1180

rem Authenticated HTTPS server:
set HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

### <a name="bash"></a>[<span data-ttu-id="3b48d-112">bash</span><span class="sxs-lookup"><span data-stu-id="3b48d-112">bash</span></span>](#tab/bash)

```bash
# Non-authenticated HTTP server:
HTTP_PROXY=http://10.10.1.10:1180

# Authenticated HTTP server:
HTTP_PROXY=http://username:password@10.10.1.10:1180

# Non-authenticated HTTPS server:
HTTPS_PROXY=http://10.10.1.10:1180

# Authenticated HTTPS server:
HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

---
